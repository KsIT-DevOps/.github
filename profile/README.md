# 健康深耕團隊（KsIT-DevOps）資訊組開發指引

歡迎來到健康深耕團隊專案版控中心。本組織負責健康示範中心系統現代化、IoT 健康鏡遠端監控代理程式（MirrorAgent）及相關周邊服務之開發與維運。

本指引旨在提供團隊成員清晰、敏捷的 Git 開發與協作準則。所有成員透過加入組織「健康深耕資訊團隊（Team）」統一獲取專案寫入權限。

---

## 核心版控準則

1. **統一 Team 授權**
   - 專案存取與推送權限統一由組織內的「健康深耕資訊團隊」管理，新成員加入 Team 後即自動取得各專案之讀寫權限。
2. **先拉取、後開發、再推送**
   - 每次開始開發前與推送前，務必先執行 `git pull` 同步最新程式碼，避免造成非預期的衝突。
3. **推行清晰提交紀錄**
   - 保持小步提交（Small Commits），每次提交訊息（Commit Message）需具備明確動詞與修改範疇。
4. **自主測試後再推送**
   - 本地端需先通過建置（Build）與基本功能測試，確認無誤後再將變更推送到遠端倉庫。

---

## 日常開發流程 (SOP)

### 1. 同步最新主線
```bash
# 切換至 main 分支並拉取最新程式碼
git checkout main
git pull origin main
```

### 2. 本地開發與變更追蹤
```bash
# 查看變更檔案狀態
git status

# 將變更檔案加入暫存區
git add .

# 提交變更並撰寫具體說明
git commit -m "feat: 實作機台狀態回傳與心跳監控邏輯"
```

### 3. 解決潛在衝突並推送到遠端
```bash
# 推送前再次確認與遠端同步
git pull origin main

# 推送至遠端 main 分支
git push origin main
```

> **建議**：若為多日長工期或實驗性較高的功能開發，建議切出個人功能分支（如 `feature/mirror-sync`）開發，告一段落後再本地合併回 `main` 推送。

---

## Commit 訊息格式建議

提交訊息建議採用簡潔的 Conventional Commits 格式：

| 類型前綴 | 適用情境 | 範例 |
| :--- | :--- | :--- |
| `feat:` | 新增功能、模組或 API 端點 | `feat: add heartbeat check endpoint` |
| `fix:` | 修復系統缺陷、例外狀況 | `fix: resolve socket reconnect timeout` |
| `refactor:` | 程式碼重構、效能優化（不影響原有邏輯） | `refactor: optimize sql query execution` |
| `chore:` | 調整設定檔、依賴套件或輔助腳本 | `chore: update appsettings config` |
| `docs:` | 新增或修訂文件、註解 | `docs: update deployment steps` |

---

## 核心專案清單

- **MirrorAgent**：現場健康鏡用戶端代理程式（Edge Agent）與中央監控服務。
- **MirrorAgentTool**：機台維護、部署與測試工具包。

---

## 技術支援與緊急窗口

- **技術負責人**：Leo (leo522)
- 若遇分支嚴重衝突、程式碼覆蓋或環境建置問題，請即刻於團隊群組通報處理。
