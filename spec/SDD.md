# Ether.fi Vault LTV 監控自助平台（n8n Webhook 版）規格書

## 1. 核心目標

建立一個「純前端＋n8n workflow」架構，讓使用者可以自助輸入 Vault 監控參數，無需帳號註冊或中心化後端，最大程度降低資安與維運負擔，並確保每位用戶的資料全自主、私有。

---

## 2. 關鍵功能需求

### 2.1 前端參數輸入介面

- 支援 Web 表單、Google Form 或 Notion 作為使用者參數收集入口
- 必填欄位：
  - Vault 地址（vaultAddress）：0x 用戶個人智能合約地址
  - 借款金額（borrowedAmount）：現有借貸 USD
  - 各幣種安全LTV百分比（safeLTVPercent）：USDC、LiquidUSD、ETH…
  - 警示門檻（warningThreshold）：如 0.05
  - 推播通知設定（Telegram Chat ID、Email）

### 2.2 參數推送到 n8n workflow

- 表單送出即 HTTP POST 到 n8n Webhook 節點
- n8n workflow 直接取用參數，開始資產查詢、警戒判斷、推播通知

### 2.3 n8n 監控主流程

- 查詢 Vault address 的鏈上資產狀況（EtherScan、Alchemy等API）
- 抓取最新市價（CoinGecko等API）
- 依自訂 LTV 計算安全線、比對當前借款
- 防呆判斷：若安全線低於借款、或接近警戒門檻，自動執行下游推播
- 通知內容包含 Vault、資產明細、安全線、警戒等資訊
- 支援 Telegram/Email多通道推播

### 2.4 自動化排程（選擇性）

- 通過 n8n workflow Schedule node 定時執行（如每5分鐘）

---

## 3. 資安與隱私規範

- 用戶所有敏感參數（Vault、通知資訊等）僅於個人 n8n 實例內使用
- 系統不存取私鑰、助記詞、帳密等資金/身份憑證
- 管理者不接觸／保管任何使用者資料
- 若大家共用 n8n 云端平台，須明確分隔各人 webhook/參數，避免洩漏與混用

---

## 4. 協作與部署模式

### 4.1 最小維運模式

- 每位用戶建議自架、自註冊自己的 n8n 實例（本地或私人雲）
- 管理者僅提供 workflow JSON、前端模板、教學
- 開源 repo 用於更新、互動與討論，推廣去中心化自助協作

### 4.2 多人協作（開放式）

- 開源 workflow、使用說明同步發佈 GitHub
- 參數範例以 config-example.json or README.md 補充
- Pull Request／Issue 協作新功能與維護
- 需明確標註資安責任歸個人、不提供資金保管

---

## 5. 使用教學與維護

- 使用者：自己部署 n8n，匯入 workflow，設置 webhook
- 前端：根據說明填寫 Vault、安全 LTV、警戒參數、推播資料，送出到對應 webhook 即可自動執行
- 管理者：僅維護 workflow 範本及文件，不參與個人資料管理

---

## 6. 限制說明

- 本工具僅做參考資產監控，不構成財務建議
- 僅支持鏈上公開 Vault，不涉及 Web2 帳號整合
- 用戶資安由個人 n8n 全權掌管

---

## 7. 版本管理

- 重大變更均記錄在 CHANGELOG.md
- 使用者需自行跟進 workflow 最新版本，依說明檔更新

---

**本規格書適用於推動去中心化、低資安壓力、社群友善的 Ether.fi Vault 自動監控推播平台，工作流程與參數皆由用戶全自主配置。**
