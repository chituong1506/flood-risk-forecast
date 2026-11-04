# API contract (bản nháp, chốt ở CP0 - cuối tuần 1)

Quy ước chung: `segment_id` là chuỗi dùng chung cho cả nhóm; thời gian theo ISO 8601 có timezone; xác suất trong khoảng 0-1.

## 1. GET /forecast/{segment_id}
Trả risk cho h1..h6.
```json
{
  "segment_id": "seg_001",
  "issued_at": "2026-11-04T08:00:00+07:00",
  "model_version": "mock-0",
  "horizons": [
    {"h": 1, "probability": 0.12, "level": "green"},
    {"h": 2, "probability": 0.25, "level": "yellow"},
    {"h": 3, "probability": 0.41, "level": "orange"},
    {"h": 4, "probability": 0.58, "level": "red"},
    {"h": 5, "probability": 0.60, "level": "red"},
    {"h": 6, "probability": 0.55, "level": "red"}
  ]
}
```

## 2. GET /map/risks
```json
{
  "issued_at": "2026-11-04T08:00:00+07:00",
  "segments": [
    {"segment_id": "seg_001", "level": "orange", "probability": 0.41, "horizon": 3}
  ]
}
```

## 3. POST /reports
```json
{
  "segment_id": "seg_001",
  "status": "flooded",
  "lat": 10.7769,
  "lng": 106.7009,
  "observed_at": "2026-11-04T08:10:00+07:00",
  "note": "Nước ngập ngang bánh xe"
}
```

## 4. GET /reports/{segment_id}
```json
{
  "segment_id": "seg_001",
  "reports": [
    {"id": 1, "status": "flooded", "observed_at": "2026-11-04T08:10:00+07:00", "verification": "pending"}
  ]
}
```

## 5. GET /forecast/{segment_id}/explanation
```json
{
  "segment_id": "seg_001",
  "horizon": 3,
  "top_features": [
    {"feature": "rain_last_3h", "contribution": 0.18},
    {"feature": "forecast_rain_h3", "contribution": 0.11}
  ],
  "note": "Đóng góp của đặc trưng vào dự đoán, không phải quan hệ nhân quả."
}
```

> Giá trị `level`, ngưỡng và JSON SHAP sẽ được Tuyến/Tùng chốt ở tuần 9-11; app không hard-code ngưỡng.
