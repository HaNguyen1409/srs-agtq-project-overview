# srs-agtq-project-overview

**AG-TQ** · Agent Node · phiên bản **1.2.0** · giấy phép MIT

> Vietnamese-language Claude skill — one independent, reusable service of the SRS-SOP agent pipeline. Machine-readable contract: [`skill.json`](skill.json).

Agent Node AG-TQ (Bước B8a SOP viết SRS): soạn TL-01 Tổng quan dự án (tầm nhìn & phạm vi) ngay cuối Pha A theo bố cục MECE 9 mục, mỗi mục trả lời một câu hỏi — bối cảnh, mục tiêu & lợi ích nối với công việc JTBD và tiêu chí đo, tầm nhìn, phạm vi tách 3 nhóm loại trừ nhau (trong / ngoài / chờ quyết định, mỗi mã yêu cầu khách đúng một nhóm), bên liên quan theo nhóm, giả định & ràng buộc, tiêu chí thành công (nơi duy nhất có chỉ số và ngưỡng), rủi ro, xác nhận. Không chép hiện trạng phần mềm hay ánh xạ vai trò ACT (thuộc AG-MT). Dùng khi cần TL-01 hoặc khi cập nhật TL-01 sau B9/B17.

## Hợp đồng giao tiếp

Skill là một dịch vụ độc lập, ghép lỏng: nhận đầu vào và trả đầu ra dưới dạng tài liệu/JSON mô tả trong [`SKILL.md`](SKILL.md), không gọi trực tiếp skill khác và không gắn với dự án cụ thể. Dùng riêng lẻ, hoặc ghép qua bộ điều phối [`srs-sop-pipeline`](https://github.com/HaNguyen1409/srs-sop-pipeline).

| Bước SOP | Việc | Loại | Nhận từ | Chuyển tới |
|---|---|---|---|---|
| 8a | Tổng quan dự án — TL-01 bản 0.1 (bố cục MECE 9 mục: bối cảnh, mục tiêu & lợi ích, tầm nhìn, phạm vi trong/ngoài/chờ quyết định, bên liên quan, giả định & ràng… | Agent | B1, B3, B5, B6, (B8), (B5a) | Khách (gửi kèm phiếu câu hỏi B6), B9; cập nhật sau B9 vòng 1 và B17; ký cùng SRS ở B24 |

**Sản phẩm đầu ra:** TL-01

**Skill phía trước (cấp đầu vào):** [`srs-ag01-transcript-summary`](https://github.com/HaNguyen1409/srs-ag01-transcript-summary) `^2.0.0` · [`srs-ag03-gap-analysis`](https://github.com/HaNguyen1409/srs-ag03-gap-analysis) `^2.2.1` · [`srs-ag05-feature-matrix`](https://github.com/HaNguyen1409/srs-ag05-feature-matrix) `^2.0.0` · [`srs-agmt-functional-matrix`](https://github.com/HaNguyen1409/srs-agmt-functional-matrix) `^1.2.0`

**Skill phía sau (dùng đầu ra):** [`srs-ag03-gap-analysis`](https://github.com/HaNguyen1409/srs-ag03-gap-analysis) `^2.2.1` · [`srs-ag06-business-model`](https://github.com/HaNguyen1409/srs-ag06-business-model) `^1.5.0` · [`srs-ag09-demo-feedback-triage`](https://github.com/HaNguyen1409/srs-ag09-demo-feedback-triage) `^1.0.0`

## Cài đặt

**Claude Code** — clone đúng phiên bản vào thư mục skill:

```bash
git clone --branch v1.2.0 https://github.com/HaNguyen1409/srs-agtq-project-overview.git ~/.claude/skills/srs-agtq-project-overview
```

Nâng cấp: `git -C ~/.claude/skills/srs-agtq-project-overview fetch --tags && git -C ~/.claude/skills/srs-agtq-project-overview checkout v<phiên-bản-mới>`.

**claude.ai / Claude Desktop** — tải `srs-agtq-project-overview-v1.2.0.zip` ở trang [Releases](https://github.com/HaNguyen1409/srs-agtq-project-overview/releases) rồi tải lên ở phần Skills trong cài đặt.

**Cả bộ** — xem [`srs-sop-skills`](https://github.com/HaNguyen1409/srs-sop-skills) (cài toàn bộ skill theo phiên bản đã khoá).

## Quản lý phiên bản

Theo [SemVer](https://semver.org/lang/vi/), áp cho hợp đồng giao tiếp của skill:

| Tăng | Khi |
|---|---|
| MAJOR | Đổi hợp đồng làm vỡ skill phía sau: đổi/bỏ trường JSON, đổi hệ mã ID, đổi bố cục tài liệu đầu ra |
| MINOR | Thêm khả năng tương thích ngược: trường tuỳ chọn, mục mới, chế độ mới |
| PATCH | Sửa câu chữ, sửa lỗi, làm rõ luật mà không đổi đầu ra |

Phát hành: sửa `SKILL.md` → tăng `version` trong frontmatter, `VERSION`, `skill.json` → thêm mục vào [`CHANGELOG.md`](CHANGELOG.md) → `python tools/check_skill.py` → commit → `git tag -a vX.Y.Z -m "vX.Y.Z"` → `git push --follow-tags`. GitHub Actions kiểm lại, chạy test và đính kèm zip vào Release.

## Giấy phép

MIT — xem [`LICENSE`](LICENSE).
