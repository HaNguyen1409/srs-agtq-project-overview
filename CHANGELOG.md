# Changelog

Mọi thay đổi đáng kể của skill ghi ở đây. Định dạng theo [Keep a Changelog](https://keepachangelog.com/vi/1.1.0/), phiên bản theo [SemVer](https://semver.org/lang/vi/).

## [Unreleased]

## [1.2.0] - 2026-11-26

### Changed

- Thêm mục «Quy tắc viết cho người đọc»: viết cho 11 nhóm người đọc, câu dẫn không nói quy trình nội bộ, mọi viết tắt và tiền tố mã có trong glossary/id_legend, trạng thái in nhãn thường, một ký hiệu một nghĩa; ký hiệu bước chưa có nguồn đổi từ «(GĐ)» sang «(suy luận)».

## [1.1.0] - 2026-11-25

### Added

- Tách thành repo độc lập (microservice skill): `skill.json` khai báo hợp đồng giao tiếp và skill phụ thuộc, CI kiểm tính nhất quán, Release tự đóng zip.
- Ẩn danh hoá: bỏ tham chiếu tới dự án áp dụng cụ thể; skill dùng được cho mọi dự án.
