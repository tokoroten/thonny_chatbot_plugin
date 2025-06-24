# Thonny AI Chat Plugin (thonny-chatbot-plugin)

[![PyPI version](https://badge.fury.io/py/thonny-chatbot-plugin.svg)](https://badge.fury.io/py/thonny-chatbot-plugin)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Python Versions](https://img.shields.io/pypi/pyversions/thonny-chatbot-plugin.svg)](https://pypi.org/project/thonny-chatbot-plugin/)

A plugin for Thonny IDE that provides an AI chat interface. It allows you to interact with Large Language Models (LLMs) directly within Thonny, get code explanations, suggestions, or have general conversations.

![ezgif-2c438ab725b002](https://github.com/user-attachments/assets/4edd34cf-7832-4af2-b35d-cebfd58fb8db)

## ✨ Features

* **Integrated Chat Interface:** AI chat window directly in Thonny's side panel
* **API Configuration:** Configure AI service API URL, API Key, and model selection (e.g., OpenAI API, local Ollama, or other compatible APIs)
* **Model List Retrieval:** Automatically fetch available models from configured API URL
* **Streaming Responses:** AI responses display in real-time without waiting for complete generation
* **Conversation History:** Records current conversation history (Note: history is not saved after closing Thonny)
* **Clear Conversation:** Button to quickly clear chat history
* **System Language Prompt:** Automatically detects system language and prompts AI to respond in that language
* **Markdown Rendering:** Supports basic Markdown formatting (bold, italic, code blocks)
* **Chat Content Copy:** Right-click in chat window to:
  * Copy selected text
  * Copy entire code block
  * Copy entire message (raw Markdown or plain text)
* **Editor Integration (Explain Selection):**
  * Select text in code editor, right-click menu shows "🤖Explain Selection (AI Chat)" option
  * Click to send selected text to AI chat window for explanation
* **Shell Integration (Explain Selection):**
  * Select text in Shell window, right-click menu also shows "🤖Explain Selection (AI Chat)" option
  * Similarly sends selected text to AI chat window for explanation
* **Dedicated Settings Menu:** Adds "AI" menu to Thonny main menu with "Settings..." item for easy access

## 📦 Installation

Two installation methods:

1. **Via Thonny Plugin Manager (Recommended):**
   * Open Thonny IDE
   * Go to `Tools` > `Manage plug-ins...`
   * Search for `thonny-chatbot-plugin`
   * Click Install
   * **Completely close and restart Thonny IDE** to load the plugin

2. **Via pip:**
   * Open your system terminal or command prompt
   * Run `pip install thonny-chatbot-plugin`
   * **Completely close and restart Thonny IDE** to load the plugin

## 🚀 Usage

1. **Configure API:**
   * After installation and restarting Thonny, you'll see a new `AI` menu in the main menu
   * Click `AI` > `Settings...` to open the settings dialog
   * **API URL:** Enter your AI service endpoint
     * e.g., OpenAI API: `https://api.openai.com/v1`
     * e.g., Local Ollama (default): `http://localhost:11434/api` (please verify your Ollama endpoint)
     * For OpenAI-compatible APIs, usually ends with `/v1`
   * **API Key:** Enter your API key. For local services like Ollama, key may not be required - leave empty or enter any character (like "ollama")
   * **Model:**
     * Click `Refresh Models` button - the plugin will attempt to fetch model list from your provided API URL
     * After success, select your desired model from the dropdown
   * Click `Save & Close`

2. **Open Chat Window:**
   * After configuration, the AI Chat Interface should appear in one of Thonny's panel areas (default registered in `w` - West/left side)
   * If not visible, check `View` menu to ensure `AI Chat Interface` is checked. If still not visible, try restarting Thonny again

3. **Start Chatting:**
   * Type your message in the input box at the bottom
   * Press `Ctrl + Enter`, `Shift + Enter` (Windows/Linux) or `Command + Return` (macOS) or click `Send` button to send message
   * AI responses will stream in the chat window

4. **Use Explain Selection:**
   * Select a piece of code or text in Thonny's code editor or Shell
   * Right-click on the selected text
   * Choose `🤖Explain Selection (AI Chat)`
   * Chat window will automatically display and send your request to AI

5. **Other Operations:**
   * Click `Clear` button at the bottom of chat window to clear current conversation history
   * Right-click on chat content to perform copy operations

## ⚙️ Configuration Details

All settings are configured in the `AI` > `Settings...` dialog:

* **API URL:** Base URL of AI service. Plugin appends `/models` to fetch model list and `/chat/completions` to send chat requests
* **API Key:** Key for authenticating your requests. Please keep it secure
* **Model:** List of available models fetched from API. You must select a model to chat

Settings are saved in Thonny's configuration file.

## 🔗 Dependencies

* `requests>=2.20.0`: For sending HTTP requests to AI API

## 🤝 Contributing

All forms of contributions are welcome! If you find bugs, have feature suggestions, or want to improve the code:

1. Please first check the [Issue Tracker](https://github.com/pondahai/thonny_chatbot_plugin/issues) for existing discussions
2. If none exists, create a new Issue to describe your problem or suggestion
3. If you want to submit code, please Fork this project, create your feature branch, make changes, then submit a Pull Request

## 📄 License

This project is licensed under the [MIT License](LICENSE).

## 🙏 Acknowledgments

* Thanks to [Thonny IDE](https://thonny.org/) for providing an excellent and easily extensible Python development environment

## Support the Project! ❤️

This project is a labor of love, and I'm incredibly grateful for your use and feedback. If you appreciate what I'm building and want to help keep it going, any contribution would be greatly appreciated! Your support allows me to dedicate more time to development, bug fixes, and new features.

Here are some ways you can contribute:  
[![paypal](https://www.paypalobjects.com/en_US/i/btn/btn_donateCC_LG.gif)](https://www.paypal.me/pondahai)