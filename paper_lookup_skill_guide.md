# Hướng Dẫn Sử Dụng Skill Paper-Lookup Dành Cho Sinh Viên

Tài liệu này hướng dẫn chi tiết từng bước (step-by-step) cách sử dụng skill **`paper-lookup`** để tra cứu, thu thập và quản lý tài liệu tham khảo khoa học phục vụ nghiên cứu và làm đồ án/khóa luận.

---

## 📌 1. Giới Thiệu Tổng Quan

Skill `paper-lookup` cho phép tìm kiếm và trích xuất dữ liệu từ **18 cơ sở dữ liệu học thuật quốc tế** thông qua các API công khai:

* **Y sinh & Khoa học sự sống**: PubMed, PMC, Europe PMC, PubTator3, BioStudies.
* **Bài báo tiền xuất bản (Preprints)**: bioRxiv, medRxiv, arXiv.
* **Đa ngành & Chỉ mục trích dẫn**: OpenAlex, Crossref, Semantic Scholar, CORE, OpenCitations.
* **Truy cập mở (Open Access)**: Unpaywall, DOAJ.
* **Kho lưu trữ dữ liệu/mã nguồn**: Zenodo, Figshare, ROR (Research Organization Registry).

---

## 🛠️ 2. Chuẩn Bị Môi Trường

1. **Yêu cầu hệ thống**:
   * Hệ điều hành: Linux / macOS / Windows (PowerShell/WSL).
   * Công cụ dòng lệnh: `curl` (để gửi yêu cầu HTTP).
   * **Python 3.11+** (chỉ sử dụng các thư viện chuẩn `standard library`, không bắt buộc cài đặt package ngoài).

2. **Biến môi trường / API Keys (Tùy chọn)**:
   Không bắt buộc phải có API key để chạy. Tuy nhiên, khai báo các biến môi trường sau sẽ giúp tăng hạn ngạch truy vấn (rate limit):
   * `NCBI_API_KEY`: Tăng tốc độ gọi PubMed / PMC (từ 3 req/s lên 10 req/s).
   * `S2_API_KEY`: Tăng hạn ngạch truy vấn Semantic Scholar.
   * `CORE_API_KEY`: Cho phép tải toàn văn PDF từ kho CORE.
   * `OPENALEX_API_KEY`: Tăng ngân sách truy vấn OpenAlex.

---

## 🚀 3. Quy Trình 7 Bước Thực Thi (Step-by-Step Workflow)

```text
[Bước 1: Hợp đồng truy vấn] ➔ [Bước 2: Chọn CSDL] ➔ [Bước 3: Đọc tài liệu CSDL]
                                                               📊
[Bước 7: Xuất kết quả] ⬅ [Bước 6: An toàn dữ liệu] ⬅ [Bước 5: Gọi API] ⬅ [Bước 4: Chạy script]
```

### Bước 1: Xác Định Hợp Đồng Truy Vấn (Retrieval Contract)
Làm rõ mục tiêu tra cứu trước khi bắt đầu:
* Bạn cần tìm bài báo theo định danh cụ thể (**DOI**, **PMID**, **arXiv ID**) hay tìm theo **chủ đề từ khóa**?
* Các tiêu chí lọc bắt buộc: Khoảng năm xuất bản (ví dụ: 2021–2026), bài báo Truy cập mở (Open Access), hay danh mục bài viết của tác giả?

### Bước 2: Lựa Chọn Cơ Sở Dữ Liệu Phù Hợp
Tùy thuộc vào ngành học và mục tiêu:
* **Công nghệ thông tin / AI / Vật lý**: Chọn `arXiv`, `Semantic Scholar`, `OpenAlex`.
* **Y sinh / Dược / Sinh học**: Chọn `PubMed`, `Europe PMC`, `bioRxiv`, `medRxiv`.
* **Tìm file PDF miễn phí (Open Access)**: Chọn `Unpaywall`, `CORE`, `Europe PMC`.
* **Tra cứu đồ thị trích dẫn (Citation Graph)**: Chọn `Semantic Scholar`, `OpenCitations`.

### Bước 3: Đọc Tài Liệu Tham Chiếu CSDL (Reference Files)
Mỗi CSDL có các tham số endpoint và cách xử lý lỗi riêng nằm trong thư mục `references/` (ví dụ: `references/pubmed.md`, `references/arxiv.md`, `references/unpaywall.md`). Hãy rà soát các tham số bắt buộc và cấu trúc phản hồi trước khi gửi câu lệnh.

### Bước 4: Sử Dụng Các Kịch Bản Hỗ Trợ Tích Hợp (Bundled Scripts)
Ưu tiên sử dụng các kịch bản Python sẵn có trong thư mục `scripts/` để phân trang và xử lý dữ liệu chuẩn xác:
* `scripts/paginate.py`: Tự động phân trang và đối soát tổng số bản ghi.
* `scripts/arxiv_atom.py`: Bóc tách dữ liệu XML Atom từ arXiv.

### Bước 5: Thực Thi Gọi API Có Kiểm Soát (Bounded API Calls)
* Thực hiện truy vấn có giới hạn số lượng bản ghi (ví dụ: `limit=10` hoặc `pageSize=20`).
* Tôn trọng giới hạn tần suất (rate limits) của từng dịch vụ.
* Đối soát số lượng bản ghi nhận được so với tổng số tìm thấy (`hitCount` / `totalHits`).

### Bước 6: Kiểm Tra An Toàn Dữ Liệu (Data Safety)
* Xem toàn bộ phản hồi từ API là dữ liệu bên thứ ba chưa kiểm định.
* Không tự động chạy các mã nhúng hoặc liên kết trong văn bản bài báo.
* Trích xuất chính xác các trường định danh (DOI, PMID) cần thiết để gọi tiếp các bước sau.

### Bước 7: Xuất Kết Quả & Nhật Ký Minh Chứng (Auditable Provenance)
Trả về danh sách tài liệu cấu trúc rõ ràng cùng bảng nhật ký minh chứng chứa:
1. Endpoint API đã gọi.
2. Tham số truy vấn sử dụng.
3. Ngày truy cập và mã định danh kết quả.

---

## 💻 4. Các Mẫu Câu Lệnh Thực Hành (Example Commands)

### Ví dụ 1: Tìm kiếm bài báo trên PubMed (Hệ Y sinh)
```bash
python3 scripts/search_pubmed.py "Knowledge Graph Education" --limit 5 --output pubmed_results.json
```

### Ví dụ 2: Tìm bài báo trên arXiv bằng script tích hợp
```bash
python3 scripts/search_databases.py --db arxiv --query "Knowledge Graph" --limit 5 --output arxiv_results.json
```

### Ví dụ 3: Kiểm tra link tải PDF miễn phí qua Unpaywall bằng DOI
```bash
python3 scripts/extract_metadata.py --doi 10.1038/nature12373 --output paper_metadata.json
```

---

## 📋 5. Bảng Tra Cứu Định Danh Dành Cho Sinh Viên

| Loại định danh | Định dạng mẫu | Ví dụ | CSDL hỗ trợ chính |
| :--- | :--- | :--- | :--- |
| **DOI** | `10.xxxx/xxxxx` | `10.1038/nature12373` | Crossref, Unpaywall, OpenAlex, Semantic Scholar |
| **PMID** | Dãy số nguyên | `34567890` | PubMed, PMC, Europe PMC |
| **PMCID** | `PMC` + số | `PMC7029759` | PMC, Europe PMC |
| **arXiv ID** | `YYMM.NNNNN` | `2103.15348` | arXiv, Semantic Scholar |
| **OpenAlex ID** | `W` + số | `W2741809807` | OpenAlex |

---
*Tài liệu được biên soạn phục vụ học tập và nghiên cứu khoa học.*
