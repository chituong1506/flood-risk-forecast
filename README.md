# Flood Risk Forecast

Dự báo xác suất rủi ro ngập 1-6 giờ tới. Đồ án nhóm 3 người.

| Thành viên | Vai trò | Thư mục |
|---|---|---|
| Tuyến | AI/ML Lead | `ml/` |
| Tùng | Backend/GIS Lead | `backend/` |
| Tường | Mobile Lead | `mobile/` |

Tài liệu chung (API contract, wireframe) nằm trong `docs/`.

## Quy ước làm việc
- Không push thẳng lên `main`, mọi thay đổi qua Pull Request.
- Tên nhánh: `mobile/MB03-map`, `backend/BE05-weather-api`, `ml/AI08-baseline`.
- Commit: `feat(mobile): MB03 hiển thị road segments`.
- Không commit API key, `.env`, keystore, file `.apk`.
- Không tự đổi cấu trúc JSON: sửa `docs/api-contract.md` bằng PR và báo cả nhóm.
