# Scientific Agent Skills: Comprehensive Setup & Usage Guide

Tài liệu hướng dẫn chi tiết từng bước (Step-by-Step) dành cho sinh viên và nghiên cứu sinh để thiết lập môi trường, cài đặt CLI host, tích hợp bộ kỹ năng nghiên cứu khoa học **Scientific Agent Skills** (`K-Dense-AI/scientific-agent-skills`) và vận hành thực tế.

---

## 📋 Mục lục
1. [Giới thiệu tổng quan](#1-giới-thiệu-tổng-quan)
2. [Bước 1: Cài đặt Môi trường Nền tảng (Python & uv)](#2-bước-1-cài-đặt-môi-trường-nền-tảng-python--uv)
3. [Bước 2: Chuẩn bị Agent Host / CLI Environment](#3-bước-2-chuẩn-bị-agent-host--cli-environment)
4. [Bước 3: Cài đặt Bộ Skill (Scientific Agent Skills)](#4-bước-3-cài-đặt-bộ-skill-scientific-agent-skills)
5. [Bước 4: Cấu hình Biến Môi trường & API Keys](#5-bước-4-cấu-hình-biến-môi-trường--api-keys)
6. [Bước 5: Thực thi & Gọi Skill trong Agent Chat / CLI](#6-bước-5-thực-thi--gọi-skill-trong-agent-chat--cli)
7. [Bước 6: Kiểm tra, Cập nhật & Xử lý Lỗi](#7-bước-6-kiểm-tra-cập-nhật--xử-lý-lỗi)

---

## 1. Giới thiệu tổng quan

Bộ kỹ năng **Scientific Agent Skills** là tập hợp các module mở rộng (skill definitions) thiết kế theo chuẩn SKILL.md. Bộ công cụ này cung cấp quy trình công tác (workflow) chuyên sâu phục vụ cho toàn bộ vòng đời nghiên cứu khoa học:
- **Tìm kiếm & Trích xuất**: `paper-lookup`, `exa-search`, `parallel-web`
- **Chuyển đổi & Đọc full-text**: `markitdown`, `paperclip`, `liteparse`
- **Phân tích & Đánh giá**: `scientific-critical-thinking`, `literature-review`
- **Quản lý trích dẫn & Viết bài**: `citation-management`, `pyzotero`, `scientific-writing`

---

## 2. Bước 1: Cài đặt Môi trường Nền tảng (Python & uv)

Bộ skill khuyến nghị sử dụng Python 3.10+ cùng công cụ quản lý gói **`uv`** (Astral) để khởi tạo và quản lý môi trường ảo độc lập cho từng tác vụ.

### 2.1. Cài đặt `uv`

- **Trên Windows (PowerShell)**:
  ```powershell
  powershell -ExecutionPolicy ByPass -c "irm https://astral.sh/uv/install.ps1 | iex"
  ```
- **Trên macOS / Linux**:
  ```bash
  curl -LsSf https://astral.sh/uv/install.sh | sh
  ```
- **Hoặc cài qua `pip`**:
  ```bash
  pip install uv
  ```

### 2.2. Kiểm tra cài đặt
Mở cửa sổ Terminal/PowerShell mới và kiểm tra:
```bash
uv --version
python --version
```

---

## 3. Bước 2: Chuẩn bị Agent Host / CLI Environment

Bạn có thể sử dụng bộ skill này trên nhiều nền tảng Agent Host khác nhau:
- **VS Code Extension / Cursor**: Mở tích hợp Agent Chat / Terminal.
- **Antigravity CLI / Gemini CLI / Claude Code / Codex**: Mở cửa sổ giao diện dòng lệnh tương tác.

---

## 4. Bước 3: Cài đặt Bộ Skill (Scientific Agent Skills)

Chọn **1 trong 3 phương thức** cài đặt sau tùy thuộc vào công cụ của bạn:

### Cách 1: Sử dụng `npx` (Khuyên dùng cho Gemini CLI, Antigravity, Cursor)
Chạy lệnh duy nhất để tải và đăng ký bộ skill vào hệ thống Agent:
```bash
npx skills add K-Dense-AI/scientific-agent-skills
```
*Lệnh này sẽ tự động tải các file kỹ năng và đặt vào thư mục cấu hình `~/.agents/skills/`.*

### Cách 2: Sử dụng GitHub CLI (`gh skill`)
Nếu máy tính của bạn đã cài đặt GitHub CLI (`gh` v2.90.0+):
```bash
# Cài đặt cho Agent Host cụ thể
gh skill install K-Dense-AI/scientific-agent-skills --agent gemini
gh skill install K-Dense-AI/scientific-agent-skills --agent cursor
gh skill install K-Dense-AI/scientific-agent-skills --agent claude-code

# Hoặc ghim phiên bản cụ thể
gh skill install K-Dense-AI/scientific-agent-skills --pin v2.72.0
```

### Cách 3: Clone thủ công từ Git (Manual Clone)
Dành cho cài đặt cục bộ ở cấp độ người dùng hoặc cấp độ dự án:
```bash
# Cài đặt cấp Hệ thống (User Level)
git clone https://github.com/K-Dense-AI/scientific-agent-skills.git ~/.agents/skills/scientific-agent-skills

# Cài đặt cấp Dự án (Project Level - trong thư mục dự án)
git clone https://github.com/K-Dense-AI/scientific-agent-skills.git .agents/skills/scientific-agent-skills
```

---

## 5. Bước 4: Cấu hình Biến Môi trường & API Keys

Một số kỹ năng truy vấn dữ liệu học thuật quốc tế cần thông tin cấu hình email hoặc API Keys để không bị giới hạn lưu lượng (rate limit).

1. Tạo tệp `.env` ngay tại thư mục gốc dự án của bạn:
   ```bash
   touch .env
   ```
2. Dán các thông số cấu hình sau vào `.env`:
   ```env
   # Email đăng ký Polite Pool cho OpenAlex và NCBI PubMed
   NCBI_EMAIL="your_student_email@university.edu.vn"
   OPENALEX_EMAIL="your_student_email@university.edu.vn"

   # API Keys dành cho tìm kiếm nâng cao & trích xuất (Nếu có)
   EXA_API_KEY="your_exa_api_key"
   ZOTERO_API_KEY="your_zotero_api_key"
   ZOTERO_USER_ID="your_zotero_user_id"
   ```

---

## 6. Bước 5: Thực thi & Gọi Skill trong Agent Chat / CLI

Khi cài đặt thành công, Agent sẽ tự động nhận diện danh mục kỹ năng khả dụng. Bạn có thể gọi skill theo các mẫu câu lệnh (prompting pattern) sau:

### Mẫu 1: Gọi đơn lẻ từng skill
```text
Hãy sử dụng skill paper-lookup để tìm kiếm 10 bài báo khoa học mới nhất về chủ đề "Educational Knowledge Graphs" trên OpenAlex và Unpaywall.
```

### Mẫu 2: Kết hợp chuỗi multi-skill (Pipeline)
```text
Thực hiện chuỗi tác vụ sau:
1. Sử dụng skill paper-lookup để thu thập danh sách 20 bài báo Open Access về chủ đề "Knowledge Graph in Education".
2. Sử dụng skill markitdown để chuyển đổi các file PDF tải về thành định dạng Markdown.
3. Sử dụng skill literature-review để lập Ma trận Tổng hợp Bằng chứng (Evidence Matrix) phân loại theo các hướng nghiên cứu chính.
```

---

## 7. Bước 6: Kiểm tra, Cập nhật & Xử lý Lỗi

### 7.1. Kiểm tra cú pháp và định dạng Skill
Để xác minh cấu trúc một skill có hợp lệ không:
```bash
uv run skills-ref validate .agents/skills/scientific-agent-skills/skills/paper-lookup
```

### 7.2. Cập nhật bộ skill lên phiên bản mới nhất
```bash
gh skill update --all
```

### 7.3. Các lỗi thường gặp & Cách khắc phục
- **Lỗi `CommandNotFoundException` / `npx not recognized`**: Đảm bảo đã cài đặt Node.js/npm và Python.
- **Lỗi `Rate Limit 429` khi tra cứu paper**: Bổ sung `OPENALEX_EMAIL` và `NCBI_EMAIL` vào tệp `.env`.
- **Lỗi `ModuleNotFoundError` khi chạy script**: Kích hoạt môi trường ảo `venv` và chạy `pip install -r requirements.txt`.

---
*Tài liệu hướng dẫn được tạo tự động cho dự án K-Dense Scientific Agent Skills.*
