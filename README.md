# AI-Exam-Generator-DTU

Ứng dụng tạo ngân hàng câu hỏi và xuất đề thi/mã đề/đáp án tự động cho giáo viên/trường học, hỗ trợ AI, xuất file Word chuẩn hội đồng.

---

## Quy trình tổng quan

1. **Quản lý chủ đề**: Tạo, upload tài liệu (PDF, DOCX, TXT) theo từng môn/nhóm chủ đề.
2. **Sinh câu hỏi tự động**: Sinh trắc nghiệm/tự luận với AI dựa trên nội dung tài liệu, phân loại mức độ, lưu vào ngân hàng.
3. **Tạo đề thi**: Sinh nhiều mã đề với số lượng câu, điểm, mức độ tự chọn; xuất file Word và đáp án chuẩn theo format hội đồng.

---

## Mục lục

1. [Cài đặt môi trường](#cài-đặt-môi-trường)
2. [Cấu trúc dự án](#cấu-trúc-dự-án)
3. [Hướng dẫn sử dụng](#hướng-dẫn-sử-dụng)
    1. [Quản lý chủ đề và nguồn tài liệu](#quản-lý-chủ-đề-và-nguồn-tài-liệu)
    2. [Sinh ngân hàng câu hỏi](#sinh-ngân-hàng-câu-hỏi)
    3. [Sinh đề thi & đáp án Word](#sinh-đề-thi--đáp-án-word)
    4. [Chỉnh sửa & xoá câu hỏi](#chỉnh-sửa--xoá-câu-hỏi)
4. [Thông tin các file Script](#thông-tin-các-file-script)
5. [Đội ngũ phát triển](#đội-ngũ-phát-triển)

---

## Cài đặt môi trường

### Clone code và cài đặt thư viện

```bash
git clone https://github.com/trannhatvinh/AI-Exam-Generator-DTU.git
cd AI-Exam-Generator-Flask-OpenAI-Groq-Docx-
python -m venv .venv
.venv\Scripts\activate       # (Windows)
# Hoặc với Linux/Mac: source .venv/bin/activate
pip install -r requirements.txt
```

> **File `requirements.txt` ví dụ:**
> ```
> flask
> python-docx
> pdfplumber
> sentence-transformers
> nltk
> rouge-score
> groq
> ```

---

## Cấu trúc dự án

```
AI-Exam-Generator-Flask-OpenAI-Groq-Docx-/
├── app.py
├── requirements.txt
├── templates/
│   └── *.html
├── static/
├── topics/
│   ├── <topic1>/
│   │   ├── uploads/
│   │   ├── exam/
│   │   └── question_bank.json
│   └── ...
├── README.md
```

---

## Hướng dẫn sử dụng

### 1. Quản lý chủ đề và nguồn tài liệu

- Vào giao diện web (`http://localhost:5000`)
- Tạo **chủ đề** mới (ví dụ: Toán, Lý, Văn...)
- Upload tài liệu nguồn (PDF, DOCX, TXT...) cho từng chủ đề

### 2. Sinh ngân hàng câu hỏi

- Chọn chủ đề
- Chọn số lượng trắc nghiệm, tự luận, mức độ và sinh bằng AI
- Xem, **sửa, xóa câu hỏi ngay trên giao diện web**

### 3. Sinh đề thi & đáp án Word

- Nhập cấu hình đề: số lượng câu, điểm, số mã đề...
- Sinh đề
- Tải về các file Word:
    - Đề từng mã đề kiểu chuẩn truyền thống
    - Đề Word format hội đồng (chuẩn Duy Tân, v.v.)
    - Đáp án Word format hội đồng

### 4. Chỉnh sửa & xoá câu hỏi

- Trong **danh sách câu hỏi của mỗi chủ đề**, nhấn nút **Sửa** trên từng câu hỏi để mở popup chỉnh sửa chi tiết.
- Popup sẽ hiển thị đầy đủ **nội dung câu hỏi, các phương án (nếu là trắc nghiệm) và đáp án** cho phép bạn sửa mọi trường liên quan dễ dàng.
- Sau khi chỉnh sửa xong, nhấn **Lưu thay đổi**, hệ thống sẽ cập nhật lại ngân hàng câu hỏi.
- Có thể xoá câu hỏi bằng nút **Xóa** bên cạnh từng câu.

---

## Thông tin các file Script

- **app.py**: Toàn bộ Flask backend, sinh câu hỏi, xuất đề.
- **templates/**: Các file HTML template cho front-end web (bao gồm cả popup sửa câu hỏi).
- **topics/**: Thư mục chứa toàn bộ tài liệu, ngân hàng, đề đã sinh theo từng chủ đề.
- **requirements.txt**: Liệt kê các thư viện cần cài đặt.
- **README.md**: Tài liệu này.

---

## Đội ngũ phát triển

| Ảnh đại diện | Tên | Vai trò | GitHub |
|:---:|:----------------|:---------------------|:-----------------------------:|
| <img src="https://avatars.githubusercontent.com/u/203066566?v=4" width="50"> | Trần Nhật Vinh | Phát triển ứng dụng + AI exam | [@trannhatvinh](https://github.com/trannhatvinh) |
| <img src="https://avatars.githubusercontent.com/u/202948270?v=4" width="50"> | Hồ Lê Viết Nin   | Review đề thi/Word/Đáp án | [@holvietnin](https://github.com/holvietnin) |
| <img src="https://avatars.githubusercontent.com/u/82451911?v=4" width="50"> | Ngô Văn Hiếu     | Xử lý dữ liệu kiểm thử | [@NgoVanHieu](https://github.com/NgoVanHieu) |

---

### **Liên hệ/Báo lỗi**  
- Nếu có lỗi về AI/giao diện/export Word hoặc cần nâng cấp module nào khác, bạn có thể tạo issue trên GitHub hoặc liên hệ [@trannhatvinh](https://github.com/trannhatvinh).