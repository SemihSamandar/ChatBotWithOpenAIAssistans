# AI CRM Chatbot

**Every conversation, a new lead.** A sales assistant for company websites that answers
visitors in natural language from your own knowledge base and files every lead into an
Airtable CRM by itself.

Built in Python on the **OpenAI Assistants API** with **RAG** (Retrieval Augmented Generation)
and custom function calling.

<p>
<a href="https://www.semihsamandar.com/projects/chatbot"><img src="https://img.shields.io/badge/Project_page-semihsamandar.com-36BCF7?style=for-the-badge&logo=googlechrome&logoColor=white" alt="Project page" /></a>
</p>

## How it works

1. A visitor opens the chat widget (`index.html`) on the website.
2. The Flask server starts a new conversation thread on the OpenAI Assistant.
3. The assistant answers from the company's knowledge file (`knowledge.docx`) using retrieval,
   guided by its own instructions (`assistant_insturctions.py`).
4. When the visitor shares their details, the assistant calls the custom `create_lead`
   function, which saves the lead into an Airtable CRM.

## API

| Method | Route | Description |
|---|---|---|
| `GET` | `/` | Serves the chat widget |
| `GET` | `/start` | Starts a new conversation thread |
| `POST` | `/chat` | Sends a message and returns the assistant's reply |

## Tech stack

| Layer | Technologies |
|---|---|
| Backend | Python, Flask, Waitress |
| AI | OpenAI Assistants API (v2), file search / RAG, function calling |
| CRM | Airtable |
| Frontend | HTML chat widget |

## Getting started

Create a `.env` file:

```env
OPENAI_API_KEY=
AIRTABLE_API_KEY=
```

CRM template: [Airtable](https://airtable.com/apph7PZRJZdsP0Skw/shrHwajwaShy0IpjH)

Run on a server:

```bash
ssh root@IPADRESS
sudo apt install python3-venv
python3 -m venv .venv
source .venv/bin/activate
pip3 install -r requirements.txt
nano .env
nohup python3 main.py
```

The app is served on port `8080`.
