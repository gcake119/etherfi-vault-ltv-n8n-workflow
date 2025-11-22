# CHANGELOG

所有重要進度與尚未完成的 n8n workflow 設定與功能更新，請見本記錄。

## [0.9.0] - 2025-11-22

### Added
- 完成基礎架構：包括 schedule trigger、workflow configuration、vault 資產查詢、幣價查詢（ETH/USDC/LiquidUSD）、安全線計算、警戒判斷、格式化警示訊息、推播（Telegram/Email）
- 前端參數流設計初步完成，核對 Ether.fi Vault + DebtManager 智能合約監控邏輯。
- README.md 與規格書根據 Airbnb 規範撰寫，同步開源上線。

### Pending / 尚未設定事項
- **DebtManager 合約查詢功能**：尚未串接 Scroll 主網 DebtManager 合約 address 與 ABI，需完成 Web3/JS節點設定查詢 getUserDebt/getBorrowLimit 等。
- **Telegram Alert**：尚未填入 Bot Token、Chat ID。
- **Email Alert**：尚未設定 SMTP，寄件人/收件人 Email。
- **API參數及驗證**：Query Vault/市價 API endpoint、API Key 等待填入（如 Etherscan/Alchemy/CoinGecko）。
- **Workflow Configuration**：Vault address、安全LTV百分比等用戶自訂參數仍需前端或表單輸入。
- **格式化通知訊息**：尚未自動帶入所有參數（Vault地址、市值、安全線、借款、清算等）。
- **參數防呆驗證**：有待補充錯誤處理與有效性檢查。
- **多用戶協作機制**：尚待接 webhook/Google Sheet 支持多人參數動態輸入。
- **文件補充**：使用教學、API 參數說明有待完善。

### Planned / 計畫中
- 整合 DebtManager 智能合約查詢至 workflow，自動更新用戶 Vault 借款/額度/清算狀況。
- 前端表單或 Google Sheet 範本開發，協助快速輸入，連結 webhook 自動監控。
- 完善動態推播內容與格式，根據各資產、自訂門檻動態警示。
- 支援多幣種與多 Vault/多用戶監控協作。
- 強化資安提示、資安邊界標註與自主管理說明。

## [Unreleased]

- 所有 Issue、Pull Request 請記錄於此
- 後續根據社群回饋優化功能與使用教學
