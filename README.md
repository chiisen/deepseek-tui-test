# deepseek-tui-test

DeepSeek-TUI 測試筆記

## 什麼是 DeepSeek-TUI？

[DeepSeek-TUI](https://github.com/Hmbown/DeepSeek-TUI) 是一個完全運行在終端裡的程式開發智能體（Coding Agent）。它讓 DeepSeek 前沿模型直接讀寫你的工作區檔案、執行 shell 命令、搜尋瀏覽網頁、管理 git、調度子智能體——全部透過快速、鍵盤驅動的 TUI 完成。

專為 **DeepSeek V4**（`deepseek-v4-pro` / `deepseek-v4-flash`）構建，原生支援 100 萬 token 上下文視窗和思考模式串流輸出。以自包含 Rust 二進制發布，開箱即帶 MCP 客戶端、沙箱和持久化任務佇列——執行時不依賴 Node.js 或 Python。

### 主要功能

- **自動模式** — `--model auto` / `/model auto` 為每一輪自動選擇模型與思考等級
- **思考模式串流輸出** — 即時觀察模型推理過程中的思維鏈展開
- **完整工具集** — 檔案操作、shell 執行、git、網頁搜尋/瀏覽、apply-patch、子智能體、MCP 伺服器
- **100 萬 token 上下文** — 上下文追蹤、手動或設定觸發的智慧壓縮，以及前綴快取（prefix-cache）成本感知
- **三種互動模式** — Plan（唯讀探索）、Agent（預設互動 + 審批）、YOLO（信任工作區自動批准）
- **推理強度檔位** — 用 `Shift+Tab` 在 `off → high → max` 之間切換
- **原生 RLM** — 利用低成本 `deepseek-v4-flash` 子任務進行批次分析和並行推理
- **會話保存與恢復** — 長任務的斷點續作
- **工作區回滾** — side-git 每回合前後快照，支援 `/restore` 和 `revert_turn`，不影響專案本身的 `.git`
- **持久化任務佇列** — 後台任務在重啟後依然存在，支援排程和長時間執行
- **HTTP/SSE 執行時 API** — `deepseek serve --http` 用於無介面智能體流程
- **MCP 協定** — 連接 Model Context Protocol 伺服器以擴展工具能力
- **LSP 診斷** — 每次編輯後透過 rust-analyzer、pyright、typescript-language-server、gopls、clangd 提供內聯錯誤/警告
- **使用者記憶** — 可選的持久化筆記注入系統提示，實現跨會話偏好保持
- **多語言 UI** — 支援 `en`、`ja`、`zh-Hans`、`pt-BR`
- **即時成本追蹤** — 按回合和會話統計 token 用量與成本估算
- **技能系統** — 可透過 GitHub 安裝的組合式指令包

## 安裝

```bash
# 1. npm — 已有 Node 最方便
npm install -g deepseek-tui

# 2. Cargo — 無需 Node
cargo install deepseek-tui-cli --locked
cargo install deepseek-tui     --locked

# 3. Homebrew — macOS 套件管理
brew tap Hmbown/deepseek-tui
brew install deepseek-tui

# 4. 直接下載 — 無需任何工具鏈
#    https://github.com/Hmbown/DeepSeek-TUI/releases

# 5. Docker
docker run --rm -it \
  -e DEEPSEEK_API_KEY \
  -v "$PWD:/workspace" \
  ghcr.io/hmbown/deepseek-tui:latest
```

> 中國大陸 npm 可加 `--registry=https://registry.npmmirror.com`

## 參考

- [DeepSeek-TUI GitHub](https://github.com/Hmbown/DeepSeek-TUI)
- [DeepSeek-TUI 簡體中文 README](https://github.com/Hmbown/DeepSeek-TUI/blob/main/README.zh-CN.md)
