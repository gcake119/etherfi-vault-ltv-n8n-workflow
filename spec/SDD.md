# Ether.fi Vault LTV 監控自助平台（n8n 監控工具版）規格書

## 1. 核心目標

建立「純前端 + n8n workflow」自動化，讓使用者可自主輸入 Vault 監控參數，系統無需集中帳號或後端，最大化個人隱私、最小化資安與營運壓力，確保資料與通知完全由用戶自己掌控。

---

## 2. 關鍵功能需求

### 2.1 前端參數輸入介面

- 支援 Web 表單、Google Form 或 Notion 作為參數收集入口
- 必填欄位：
  - Vault 地址（vaultAddress）：Ether.fi Cash 用戶獨立合約地址
  - 各幣種安全LTV百分比（safeLTVPercent）：USDC、LiquidUSD、ETH...
  - 警戒門檻（warningThreshold）：如 0.05
  - 推播通知設定（Telegram Chat ID、Email 信箱）

### 2.2 參數推送至 n8n workflow

- 表單送出即 HTTP POST 到 n8n Webhook 節點
- n8n workflow 取用參數，自動查詢資產、判斷安全線、推播警示

### 2.3 智能合約查詢與自訂條件

- 直接用官方開源 DebtManager 合約（Scroll網路）
  - 查詢 vault address：
    - 現有債務（getUserDebt）
    - 最大可借額度（getBorrowLimit）
    - 清算門檻/安全距離（getLiquidationInfo）
- 依用戶自訂安全LTV條件比對資產市值、借貸狀況
- 用戶可自訂每種資產的警示與安全參數

### 2.4 推播與定時監測

- 支援 Telegram、Email 等多種推播渠道
- n8n workflow schedule node 定時執行（建議每5-15分鐘）

---

## 3. 資安與隱私規範

- 所有敏感參數僅存於用戶私有 n8n 實例
- 不存取私鑰、密碼、Web2帳號等資料
- 管理者僅提供流程範本，不存取或管理用戶參數
- 若共用雲端平台，須分隔 webhook 與參數，避免資料外洩

---

## 4. 協作與部署模式

### 4.1 個人部署（推薦）

- 用戶自架或註冊自己的 n8n（如 Zeabur 雲端）
- 管理者只維護 workflow JSON、前端設計、說明教學
- 開源 GitHub repo，供社群持續回饋與升級

### 4.2 團隊或開放協作

- workflow JSON、教學同步開源，鼓勵 PR 與 Issue 建議
- 配合 config-example.json/README.md 提供範例
- 強調資安責任屬個人，不進行資金託管

---

## 5. 使用與維護教學

- 用戶自備 n8n 實例，匯入 workflow，設 webhook node
- 前端或表單填 vault 地址、警戒條件、推播資訊
- 測試 workflow，確認自動監控與推播流程正常
- 管理者僅維護開源範本與API教學，不涉及個人資料協作

---

## 6. 限制說明

- 僅供鏈上公開 Vault 監控，不構成財務建議
- 本工具不支援 Web2 賬號或中心化資產管理
- 資安風險完全由個人 n8n 和參數管理者負責

---

## 7. 版本管理

- 所有改動與重要升級記錄於 CHANGELOG.md
- 用戶依需求跟進 workflow 與資安設定更新

---

**本規格書適用於個人／社群開源自動監控 Ether.fi Vault 借貸工具，強調去中心化、低風險、易協作及完全自主運作。**
