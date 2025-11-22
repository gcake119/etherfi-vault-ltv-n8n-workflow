# CHANGELOG

所有重要進度與尚未完成的 n8n workflow 設定，在此紀錄。

## [0.9.0] - 2025-11-22

### Added
- 完成主要架構串連：Schedule Trigger, Workflow Configuration, Vault 資產查詢、幣價查詢（ETH/USDC/LiquidUSD）、安全線計算、警戒判斷、自動格式化警示訊息、推播（Telegram/Email）。
- 前端指令流與範本已初步設計，完整覆蓋 Ether.fi Vault 監控核心邏輯。
- CHANGLOG.md 與 README.md 框架建立，規格書同步上線。

### Pending / 尚未設定事項
- **Telegram Alert**：尚未填入 Bot Token、Chat ID。
- **Email Alert**：尚未設定 SMTP 帳號、寄件人/收件人 Email。
- **Query Vault Assets**：API endpoint、API Key 未完成設定（如 Etherscan/Alchemy）。
- **Fetch LiquidUSD Price**：API endpoint 尚未確定，可選 CoinGecko 或自訂 oracle。
- **Workflow Configuration**：Vault address、borrowedAmount、安全LTV百分比等參數需使用者自行填入。
- **格式化通知訊息**：通知內容尚未自動帶入各參數（如 Vault 地址、市值、安全線、借款）。
- **防呆驗證**：參數有效性檢查尚未完成，需補充錯誤處理和提示。
- **多用戶協作支持**：尚未導入 webhook/Google Sheet 多人協作參數源。
- **文件補充**：使用教學、API參數設定說明待完善。

### Planned / 計畫中
- 完善所有參數提示及自動化驗證，提升新手上手體驗。
- 開發前端表單或 Google Sheet 範本，供快速輸入並接 webhook。
- 完善通知格式模板，讓警示訊息自動帶入所有動態資訊。
- 增加多幣種與多 Vault 支援。
- 增加安全性提示與資安邊界說明。

## [Unreleased]

- Issue追蹤與 Pull Request 變更請記錄於此
- 下一步依協作群回饋持續優化
