# 資料整合 API 文檔

歡迎使用資料整合 API！本 API 提供專案相關資料查詢與整合服務，讓您能夠輕鬆存取專案資訊、設備數據等功能。

## 快速開始

### 1. 取得 API 金鑰

在開始使用 API 之前，您需要先取得 API 金鑰：

1. 登入 [智能助理平台](https://web.i-daka.com)
2. 前往「使用者」→「API 金鑰管理」
3. 建立新的 API 金鑰並妥善保存

詳細說明請參考 [API 金鑰管理指南](docs/guides/api-key-management.md)

### 2. 開始使用 API

```bash
curl -X GET "https://api.example.com/v1/projects" \
  -H "X-API-Key: your_api_key_here"
```

詳細的認證說明請參考 [認證機制文檔](docs/getting-started/authentication.md)

## 文檔導覽

### 入門指南

- [認證機制](docs/getting-started/authentication.md) - 了解如何使用 API 金鑰進行認證

### 使用指南

- [API 金鑰管理](docs/guides/api-key-management.md) - 學習如何建立、管理和撤銷 API 金鑰

### API 參考

- [OpenAPI 規範](api-schema.yml) - 完整的 API 規範文檔

## 主要功能

### 專案管理

- 取得所有專案列表
- 查詢特定專案詳細資訊
- 取得專案設備列表

### 即時數據

- 即時在場人數統計
- 當日進出場人次
- 設備即時數據

## 技術支援

如有任何問題或需要協助，請聯繫：

- 技術文檔：請參考本文檔的各個章節
- 問題回報：請聯繫 iDaka 技術窗口

## 版本資訊

**目前版本：** 1.0.0

---

**© 2025 iDaka. All rights reserved.**
