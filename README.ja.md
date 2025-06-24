# Thonny AI チャットプラグイン (thonny-chatbot-plugin)

[![PyPI version](https://badge.fury.io/py/thonny-chatbot-plugin.svg)](https://badge.fury.io/py/thonny-chatbot-plugin)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Python Versions](https://img.shields.io/pypi/pyversions/thonny-chatbot-plugin.svg)](https://pypi.org/project/thonny-chatbot-plugin/)

Thonny IDE 内で AI チャットインターフェースを提供するプラグインです。Thonny 内で直接大規模言語モデル (LLM) とやり取りし、コードの説明や提案を受けたり、一般的な会話をすることができます。

![ezgif-2c438ab725b002](https://github.com/user-attachments/assets/4edd34cf-7832-4af2-b35d-cebfd58fb8db)

## ✨ 機能

* **統合チャットインターフェース：** Thonny のサイドパネルに AI チャットウィンドウを直接表示
* **API 設定：** AI サービスの API URL、API キー、モデル選択を設定可能（例：OpenAI API、ローカル Ollama、その他互換 API）
* **モデルリスト取得：** 設定した API URL から利用可能なモデルを自動取得
* **ストリーミングレスポンス：** AI の応答が完全に生成されるのを待たずにリアルタイムで表示
* **会話履歴：** 現在の会話履歴を記録（注：Thonny を閉じると履歴は保存されません）
* **会話クリア：** チャット履歴を素早くクリアするボタン
* **システム言語プロンプト：** システム言語を自動検出し、AI がその言語で応答するようプロンプト
* **Markdown レンダリング：** 基本的な Markdown フォーマットをサポート（太字、斜体、コードブロック）
* **チャット内容のコピー：** チャットウィンドウで右クリックして：
  * 選択したテキストをコピー
  * コードブロック全体をコピー
  * メッセージ全体をコピー（生の Markdown またはプレーンテキスト）
* **エディタ統合（選択範囲の説明）：**
  * コードエディタでテキストを選択後、右クリックメニューに「🤖Explain Selection (AI Chat)」オプションが表示
  * クリックすると選択したテキストを AI チャットウィンドウに送信して説明を要求
* **シェル統合（選択範囲の説明）：**
  * シェルウィンドウでテキストを選択後、右クリックメニューにも「🤖Explain Selection (AI Chat)」オプションが表示
  * 同様に選択したテキストを AI チャットウィンドウに送信して説明を要求
* **専用設定メニュー：** Thonny のメインメニューに「AI」メニューを追加し、「Settings...」項目で簡単にアクセス可能

## 📦 インストール

2つのインストール方法：

1. **Thonny プラグインマネージャー経由（推奨）：**
   * Thonny IDE を開く
   * `ツール` > `プラグイン管理...` へ移動
   * `thonny-chatbot-plugin` を検索
   * インストールをクリック
   * **Thonny IDE を完全に閉じて再起動**してプラグインを読み込む

2. **pip 経由：**
   * システムのターミナルまたはコマンドプロンプトを開く
   * `pip install thonny-chatbot-plugin` を実行
   * **Thonny IDE を完全に閉じて再起動**してプラグインを読み込む

## 🚀 使い方

1. **API の設定：**
   * インストールして Thonny を再起動すると、メインメニューに新しい `AI` メニューが表示されます
   * `AI` > `Settings...` をクリックして設定ダイアログを開く
   * **API URL：** AI サービスのエンドポイントを入力
     * 例：OpenAI API: `https://api.openai.com/v1`
     * 例：ローカル Ollama（デフォルト）: `http://localhost:11434/api`（Ollama のエンドポイントを確認してください）
     * OpenAI 互換 API の場合、通常 `/v1` で終わります
   * **API Key：** API キーを入力。Ollama のようなローカルサービスではキーが不要な場合があります - 空のままにするか任意の文字（「ollama」など）を入力
   * **Model：**
     * `Refresh Models` ボタンをクリック - プラグインが提供された API URL からモデルリストの取得を試みます
     * 成功後、ドロップダウンから使用したいモデルを選択
   * `Save & Close` をクリック

2. **チャットウィンドウを開く：**
   * 設定後、AI チャットインターフェースが Thonny のパネルエリアのいずれかに表示されるはずです（デフォルトは `w` - West/左側に登録）
   * 表示されない場合は、`表示` メニューで `AI Chat Interface` がチェックされているか確認。それでも表示されない場合は、Thonny を再度再起動してみてください

3. **チャットを開始：**
   * 下部の入力ボックスにメッセージを入力
   * `Ctrl + Enter`、`Shift + Enter`（Windows/Linux）または `Command + Return`（macOS）を押すか、`Send` ボタンをクリックしてメッセージを送信
   * AI の応答がチャットウィンドウにストリーミング表示されます

4. **選択範囲の説明を使用：**
   * Thonny のコードエディタまたはシェルでコードやテキストを選択
   * 選択したテキスト上で右クリック
   * `🤖Explain Selection (AI Chat)` を選択
   * チャットウィンドウが自動的に表示され、リクエストを AI に送信

5. **その他の操作：**
   * チャットウィンドウ下部の `Clear` ボタンをクリックして現在の会話履歴をクリア
   * チャット内容で右クリックしてコピー操作を実行

## ⚙️ 設定の詳細

すべての設定は `AI` > `Settings...` ダイアログで行います：

* **API URL：** AI サービスのベース URL。プラグインはモデルリスト取得のために `/models` を、チャットリクエスト送信のために `/chat/completions` を追加します
* **API Key：** リクエストを認証するためのキー。安全に保管してください
* **Model：** API から取得した利用可能なモデルのリスト。チャットするにはモデルを選択する必要があります

設定は Thonny の設定ファイルに保存されます。

## 🔗 依存関係

* `requests>=2.20.0`: AI API への HTTP リクエスト送信用

## 🤝 貢献

あらゆる形での貢献を歓迎します！バグを見つけた場合、機能の提案がある場合、またはコードを改善したい場合：

1. まず [Issue Tracker](https://github.com/pondahai/thonny_chatbot_plugin/issues) で既存の議論があるか確認してください
2. 存在しない場合は、新しい Issue を作成して問題や提案を説明してください
3. コードを提出したい場合は、このプロジェクトをフォークし、機能ブランチを作成し、変更を加えてから Pull Request を提出してください

## 📄 ライセンス

このプロジェクトは [MIT ライセンス](LICENSE)の下でライセンスされています。

## 🙏 謝辞

* 優れた拡張しやすい Python 開発環境を提供してくださった [Thonny IDE](https://thonny.org/) に感謝します

## プロジェクトをサポート！ ❤️

このプロジェクトは愛情を込めて作られており、皆様のご利用とフィードバックに心から感謝しています。私が構築しているものを評価し、継続を支援したいと思われる場合、どんな貢献でも大歓迎です！皆様のサポートにより、開発、バグ修正、新機能により多くの時間を費やすことができます。

貢献する方法：  
[![paypal](https://www.paypalobjects.com/en_US/i/btn/btn_donateCC_LG.gif)](https://www.paypal.me/pondahai)