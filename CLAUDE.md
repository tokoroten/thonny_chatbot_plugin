# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a Thonny IDE plugin that provides an AI chatbot interface. The plugin allows users to interact with LLMs (OpenAI API, Ollama, etc.) directly within Thonny IDE, with features like code explanation via context menus and streaming responses.

## Key Development Commands

- **Installation for development:** Install Thonny IDE, then copy the `thonnycontrib` folder to Thonny's plugins directory or use `pip install -e .` in the project root
- **Testing:** No automated tests currently exist. Manual testing is done by loading the plugin in Thonny
- **Distribution:** Published to PyPI as `thonny-chatbot-plugin`

## Architecture Overview

### Plugin Structure
- **Entry point:** `thonnycontrib/AIChatView.py:load_plugin()` - Called by Thonny to register the plugin
- **Main class:** `AIChatView` - Inherits from `ttk.Frame`, manages the entire chat UI
- **Settings:** `SettingsDialog` - Modal dialog for API configuration
- **Configuration keys:** Stored in Thonny's settings system:
  - `plugin.ai_chat.api_url`
  - `plugin.ai_chat.api_key`
  - `plugin.ai_chat.model`

### Integration Points
1. **UI Registration:** Plugin registers as a view in Thonny's west panel
2. **Menu System:** Adds "AI" menu to main menu bar with settings option
3. **Context Menus:** Monkey patches Shell's `populate_menu()` and adds to editor's context menu for "Explain Selection" feature
4. **Threading Model:** Uses worker threads with queue-based communication for non-blocking API calls

### API Communication
- Supports OpenAI-compatible APIs (endpoints: `/models` for listing, `/chat/completions` for chat)
- Handles both streaming and non-streaming responses
- Error handling with user-friendly messageboxes and detailed logging

### UI Components
- **Chat display:** Custom text widget with markdown rendering (bold, italic, code blocks)
- **Input area:** Multi-line text widget with keyboard shortcuts (Ctrl+Enter to send)
- **Context menus:** Copy functionality for messages, code blocks, and selected text

## Important Patterns

1. **Thread Safety:** All UI updates from worker threads use `self.after()` method
2. **State Management:** Manual tracking of view visibility and cleanup on destruction
3. **Error Handling:** Comprehensive try-except blocks with logging and user notifications
4. **Markdown Parsing:** Regex-based parsing for basic markdown formatting
5. **Thonny Integration:** Follows Thonny's plugin conventions (namespace, registration, cleanup)

## Development Notes

- Code contains extensive inline comments in both Chinese and English
- No external dependencies except `requests` for HTTP communication
- Plugin must be reloaded by restarting Thonny after changes
- API configuration is persistent across Thonny sessions