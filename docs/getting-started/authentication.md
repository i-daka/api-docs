# 認證機制

資料整合 API 使用 **API 金鑰 (API Key)** 進行身份驗證,確保只有授權的應用程式能夠存取您的資料。

## 認證方式

### HTTP Header 認證

所有 API 請求都必須在 HTTP Header 中包含有效的 API 金鑰:

```http
X-API-Key: your_api_key_here
```

## 完整請求範例

### cURL

```bash
curl -X GET "https://api.example.com/v1/projects" \
  -H "X-API-Key: idaka_xxxxxxxxxxxxxxxxxxxxxxxxxxxx"
```

### Python (requests)

```python
import requests

api_key = "idaka_xxxxxxxxxxxxxxxxxxxxxxxxxxxx"
headers = {
    "X-API-Key": api_key
}

response = requests.get(
    "https://api.example.com/v1/projects",
    headers=headers
)

print(response.json())
```

### JavaScript (fetch)

```javascript
const apiKey = "idaka_xxxxxxxxxxxxxxxxxxxxxxxxxxxx";

fetch("https://api.example.com/v1/projects", {
  headers: {
    "X-API-Key": apiKey
  }
})
  .then(response => response.json())
  .then(data => console.log(data))
  .catch(error => console.error("Error:", error));
```

### JavaScript (Node.js with axios)

```javascript
const axios = require('axios');

const apiKey = "idaka_xxxxxxxxxxxxxxxxxxxxxxxxxxxx";

axios.get("https://api.example.com/v1/projects", {
  headers: {
    "X-API-Key": apiKey
  }
})
  .then(response => console.log(response.data))
  .catch(error => console.error("Error:", error));
```

## 取得 API 金鑰

在開始使用 API 之前,您需要先建立 API 金鑰:

1. 登入 [智能助理平台](https://web.i-daka.com)
2. 前往至「使用者」→「API 金鑰管理」
3. 點擊「新增金鑰」按鈕
4. 填寫金鑰資訊並選擇專案範圍
5. 建立後立即複製並妥善保存金鑰

詳細步驟請參考 [API 金鑰管理指南](../guides/api-key-management.md)。

## 認證錯誤處理

### 401 Unauthorized - 未提供 API Key

**原因**: 請求中未包含 `X-API-Key` header

**回應範例**:
```json
{
  "code": 401,
  "error": "API key required"
}
```

**解決方法**: 確保在請求的 HTTP Header 中加入 `X-API-Key`

### 403 Forbidden - API Key 無效

**原因**: 提供的 API Key 無效、已撤銷或沒有存取該資源的權限

**回應範例**:
```json
{
  "code": 403,
  "error": "Invalid API key"
}
```

**解決方法**:
1. 檢查 API Key 是否正確
2. 確認 API Key 狀態為「啟用中」
3. 確認該 API Key 有存取目標專案的權限

## 安全性最佳實踐

### 1. 保護您的 API 金鑰

- **永不公開**: 不要將 API 金鑰提交到版本控制系統 (如 Git)
- **使用環境變數**: 將金鑰存放在環境變數或配置檔案中
- **定期輪換**: 定期更換長期使用的金鑰

### 2. 環境變數範例

**Linux/macOS (.bashrc 或 .zshrc)**:
```bash
export IDAKA_API_KEY="idaka_xxxxxxxxxxxxxxxxxxxxxxxxxxxx"
```

**Windows (PowerShell)**:
```powershell
$env:IDAKA_API_KEY="idaka_xxxxxxxxxxxxxxxxxxxxxxxxxxxx"
```

**Python (.env 檔案 + python-dotenv)**:
```bash
# .env 檔案
IDAKA_API_KEY=idaka_xxxxxxxxxxxxxxxxxxxxxxxxxxxx
```

```python
# Python 程式碼
from dotenv import load_dotenv
import os

load_dotenv()
api_key = os.getenv("IDAKA_API_KEY")
```

**Node.js (.env 檔案 + dotenv)**:
```bash
# .env 檔案
IDAKA_API_KEY=idaka_xxxxxxxxxxxxxxxxxxxxxxxxxxxx
```

```javascript
// JavaScript 程式碼
require('dotenv').config();
const apiKey = process.env.IDAKA_API_KEY;
```

### 3. 最小權限原則

- 為不同的應用程式或環境建立獨立的 API 金鑰
- 只授予每個金鑰必要的專案存取權限
- 生產環境與測試環境使用不同的金鑰

### 4. 監控與稽核

- 定期檢查 API 金鑰的最後使用時間
- 撤銷不再使用的舊金鑰
- 如發現異常使用,立即撤銷金鑰並建立新的

## 金鑰格式說明

API 金鑰採用以下格式:

```
idaka_xxxxxxxxxxxxxxxxxxxxxxxxxxxx
```

- `idaka`: iDaka 平台識別前綴
- 後續為隨機生成的唯一識別碼

## 下一步

- 學習如何 [管理 API 金鑰](../guides/api-key-management.md)
- 查看 [OpenAPI 規範](../../api-schema.yml) 了解可用的端點
