# Thonny Chatbot Plugin

一個為 Thonny IDE 設計的 AI 聊天介面外掛，讓您可以在 IDE 中直接與 AI 互動並解釋程式碼。

## 安裝 (Installation)

1.  開啟 Thonny > `工具 (Tools)` > `管理外掛 (Manage plug-ins)...`
2.  搜尋 `thonny-chatbot-plugin` 並安裝。
3.  **重新啟動 Thonny**。

## 設定 (Configuration)

1.  重新啟動後，點擊頂部選單 `AI` > `Settings...`。
2.  **API URL**: 輸入您的 AI 服務端點 (例如 `https://api.openai.com/v1` 或本地模型的 URL，如 `http://localhost:1234/v1`)。
3.  **API Key**: 輸入您的 API 金鑰 (如果您的服務需要)。
4.  **Model**: 點擊 `Refresh Models`，然後從下拉選單中選擇一個可用的模型。
5.  點擊 `Save & Close`。

*注意：需要存取一個相容 OpenAI API 標準的服務才能運作。*

## 使用方法 (Usage)

**聊天介面 (Chat Interface):**

*   透過 `檢視 (View)` > `AI Chat Interface` 開啟視窗。
*   在底部輸入框輸入文字，按 `Send` 或 `Ctrl/Cmd+Enter` 發送。
*   點擊 `Clear` 清除當前對話。

**解釋選取內容 (Explain Selection):**

*   在 **編輯器 (Editor)** 或 **Shell** 中選取程式碼或文字。
*   在選取的內容上 **按右鍵**。
*   選擇 `🤖Explain Selection (AI Chat)`。
*   解釋結果將顯示在聊天視窗中。

---

以下是上述 README 的英文版翻譯：

---

# Thonny Chatbot Plugin

An AI-powered chatbot plugin designed for the Thonny IDE, enabling you to interact with AI directly within the IDE and explain code.

## Installation

1. Open Thonny and go to `Tools` > `Manage plug-ins...`.
2. Search for `thonny-chatbot-plugin` and install it.
3. **Restart Thonny**.

## Configuration

1. After restarting, click `AI` > `Settings...` in the top menu.
2. **API URL**: Enter the endpoint of your AI service (e.g., `https://api.openai.com/v1` or a local model URL like `http://localhost:1234/v1`).
3. **API Key**: Enter your API key (if required by your service).
4. **Model**: Click `Refresh Models` and select an available model from the dropdown menu.
5. Click `Save & Close`.

*Note: A service compatible with the OpenAI API standard is required for the plugin to function.*

## Usage

**Chat Interface:**

- Open the window via `View` > `AI Chat Interface`.
- Enter text in the input box at the bottom, then press `Send` or `Ctrl/Cmd+Enter` to send.
- Click `Clear` to clear the current conversation.

**Explain Selection:**

- Select code or text in the **Editor** or **Shell**.
- **Right-click** on the selected content.
- Choose `🤖Explain Selection (AI Chat)`.
- The explanation will appear in the chat window.

---


