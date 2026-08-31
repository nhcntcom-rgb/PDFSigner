# PDF Signer

Phần mềm ký số tài liệu PDF cho Windows, dùng chứng thư số trong USB token.

**Tài liệu không rời khỏi máy.** Việc ký diễn ra ngay trên máy người dùng, khoá bí
mật không rời khỏi token, mất mạng vẫn ký được. Phần mềm không gửi tài liệu lên
bất kỳ máy chủ nào.

<p align="center">
  <a href="https://github.com/nhcntcom-rgb/PDFSigner/releases/latest">
    <b>⬇ Tải bản mới nhất</b>
  </a>
</p>

---

## Tải và cài

| File | Dùng khi |
|---|---|
| **`setup.exe`** | Cài bình thường. Bộ cài đầy đủ, có cả phần gỡ cài đặt. |
| `PDFSigner.zip` | Máy chặn chạy file `.exe` lạ: giải nén ra rồi chạy `PDFSigner.exe`. |
| `PDFSigner-capnhat.zip` | Gói vá — phần mềm tự tải khi cập nhật, **không cần tải tay**. |

Yêu cầu: Windows 10 hoặc mới hơn (64 bit). Bộ cài tự kèm .NET Runtime, không phải
cài thêm gì.

Bộ cài được **ký số** bằng chứng thư OV code signing. Sau khi tải, bấm chuột phải
vào `setup.exe` → **Properties → Digital Signatures** để đối chiếu nhà phát hành
trước khi chạy.

## Cập nhật

Phần mềm tự hỏi trang phát hành này xem có bản mới không, và **vá tại chỗ**: chỉ
tải phần đã đổi (vài trăm KB) rồi thay, không bắt cài lại từ đầu. Cấu hình, mẫu
chữ ký và ảnh con dấu giữ nguyên.

Muốn tự kiểm: **Cài đặt → Cập nhật phần mềm → Kiểm tra ngay**.

Gói vá tải về được kiểm hai lớp trước khi thay file — băm SHA-256 phải khớp, và
file trong gói phải ký số cùng nhà phát hành với bản đang chạy. Thiếu một trong
hai là bỏ gói.

## Làm được gì

**Ký PDF**

- Ký theo chuẩn PAdES, ghi thêm vào file (incremental) nên **chữ ký của người ký
  trước vẫn còn nguyên giá trị** — nhiều người ký nối tiếp vào một văn bản được.
- Kéo thả để đặt ô chữ ký, nhìn thấy con dấu ngay trong lúc kéo.
- Con dấu đỏ, chữ ký tay, dấu chức danh — ghép sẵn thành mẫu, ký lần sau chỉ chọn mẫu.
- Ký hàng loạt nhiều file một lượt.
- Dấu thời gian RFC3161 (TSA), kiểm chuỗi tin cậy, kiểm thu hồi CRL/OCSP.
- Xác thực chữ ký: ai ký, ký lúc nào, file có bị sửa sau khi ký không.

**Ký file cài đặt Windows**

- Ký Authenticode qua Microsoft SignTool, kèm dấu thời gian.

**Ký từ xa**

- Máy có token bật chế độ cho máy khác ký qua. Máy ở xa (kể cả macOS) ghép nối
  bằng mã 6 số, rồi ký như ký tại chỗ.
- Đường truyền TLS có ghim vân tay chứng thư; **mỗi lượt ký đều phải người giữ
  token bấm duyệt**. Khoá bí mật không bao giờ rời khỏi token.

**Khác**

- Giao diện tiếng Việt / tiếng Anh, nền sáng / nền tối.
- Chạy qua proxy của cơ quan.
- Đọc được file Office (Word, Excel) — chuyển sang PDF rồi ký.

## Câu hỏi hay gặp

**Có phải trả tiền không?** Không. Tải về dùng.

**Có gửi tài liệu của tôi đi đâu không?** Không. Phần mềm chỉ gọi ra ngoài trong
ba việc: hỏi bản mới ở trang này, xin dấu thời gian từ máy chủ TSA (nếu bật), và
kiểm thu hồi chứng thư (nếu bật). Tài liệu không đi kèm trong bất cứ việc nào.

**Windows báo "Windows protected your PC"?** Bộ cài ở đây đã ký số nên bình thường
không gặp. Nếu gặp, kiểm lại chữ ký như hướng dẫn ở trên — file tải từ nơi khác có
thể không phải bản gốc.

**Máy tôi không có token thì ký được không?** Ký qua máy khác có token — xem mục
"Ký từ xa".

**Dùng trên macOS được không?** Bản macOS ký qua máy Windows có cắm token (trên
macOS, USB token của các nhà cung cấp trong nước chưa dùng trực tiếp được).

## Liên hệ

Phần mềm do **Công ty TNHH NTCOM** phát triển.

- Địa chỉ: Số 2 Hoàng Ngọc Phách, Phường Láng, TP. Hà Nội, Việt Nam
- Điện thoại: 024 6675 5558 · Di động: 0986.397.886 (Zalo/WhatsApp/Viber)
- Email: nguyen.cuong@ntcomvn.com
- Website: https://ntcomvn.com

Lỗi hoặc góp ý: mở [Issue](https://github.com/nhcntcom-rgb/PDFSigner/issues) hoặc
gửi email.

---

<details>
<summary><b>English</b></summary>

**PDF Signer** — a desktop app for digitally signing PDF documents on Windows using
certificates stored on a USB token.

Documents never leave the machine: signing happens locally, the private key never
leaves the token, and it works offline.

Download the latest build from the
[Releases page](https://github.com/nhcntcom-rgb/PDFSigner/releases/latest).
Requires Windows 10+ (64-bit); the installer bundles the .NET runtime. Installers
are Authenticode-signed — check the publisher under *Properties → Digital
Signatures* before running.

Features: PAdES incremental signing (earlier signatures stay valid), drag-and-drop
signature placement with live seal preview, red company seals and handwritten
signature images, batch signing, RFC3161 timestamps, trust-chain and revocation
checking, signature verification, Authenticode signing via Microsoft SignTool, and
remote signing — a machine with the token approves each signature request from
remote Windows or macOS clients over pinned TLS. Vietnamese and English UI, light
and dark themes.

Developed by NTCOM Co., Ltd. Contact: nguyen.cuong@ntcomvn.com
</details>
