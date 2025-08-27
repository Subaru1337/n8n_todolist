# n8n_todolist

# 📌 Todo Automation Workflow (n8n)

This repository contains an **n8n workflow** that automates task creation in Todoist from **Telegram messages or voice notes**, with the help of **Google Gemini** for natural language understanding and **AssemblyAI** for speech-to-text.

---

## 🚀 Features

* **Telegram Trigger** → Start workflow from text or voice messages in Telegram.
* **Voice-to-Text** → Uses **AssemblyAI** API to transcribe voice notes.
* **AI Task Extraction** → Google Gemini processes messages to extract the task content and due date.
* **Todoist Integration** → Creates tasks automatically in your Todoist account.
* **Telegram Response** → Confirms task creation back in your Telegram chat.

---

## ⚙️ Requirements

Before importing and running this workflow, you’ll need:

* [n8n](https://n8n.io/) (self-hosted or cloud version)
* A **Telegram Bot Token** (via [BotFather](https://core.telegram.org/bots#botfather))
* A **Todoist account** with OAuth2 connection
* A **Google Gemini (PaLM API) key**
* An **AssemblyAI API key** for transcription

---

## 🔑 Credentials Setup

This workflow uses placeholders for credentials. You must configure them inside n8n:

1. **Telegram API**

   * Replace `(your_bot_token)` with your real bot token in the HTTP Request and URL nodes.
   * Connect your **Telegram credentials** in the *Telegram Trigger* and *Send Message* nodes.

2. **AssemblyAI**

   * Create an HTTP Header Auth credential.
   * Name: `Authorization`
   * Value: **Your AssemblyAI API key**
   * Attach it to the transcription nodes.

3. **Google Gemini (PaLM)**

   * Connect your Gemini API key in the **Message a model** node.

4. **Todoist**

   * Use OAuth2 credentials for Todoist.
   * Attach them in the **Create a task** node.

---

## 📂 How It Works

1. User sends a **text** or **voice message** in Telegram.
2. If voice, the message is sent to **AssemblyAI** → transcription text is extracted.
3. Message is passed to **Google Gemini** → AI extracts `task_content` and `due_date`.
4. Task is created in **Todoist** with the extracted details.
5. A confirmation is sent back to the **Telegram chat**.

---

## 📝 Notes

* The provided JSON file is a **template** – it does not include any real API keys.
* Replace placeholders with your own credentials.
* Do **not** share your keys or tokens publicly.

---

## ▶️ Usage

1. Import `public_todo.json` into your n8n instance.
2. Set up all required credentials as explained above.
3. Activate the workflow.
4. Start sending tasks via Telegram 🎉
