# send_email
Here’s a **README.md** draft tailored for your `mcp_email_tool.py` so it clearly explains usage, setup, and that it’s meant to be used as a **Dify MCP tool**:

---

# 📧 MCP Email Tool

This project provides an **MCP (Model Context Protocol) tool** that allows you to send emails via SMTP.
It is built with **FastMCP** and is designed to be integrated into the **[Dify AI](https://dify.ai/)** platform as a custom tool.

---

## 🚀 Features

* Send plain-text emails using SMTP.
* Secure authentication with environment variables.
* Easy integration as a tool in **Dify** via MCP.

---

## 📂 File Overview

* **`mcp_email_tool.py`** → The MCP server script for sending emails.
* **`.env`** → Stores sensitive credentials (not included in repo).

---

## ⚙️ Setup Instructions

### 1. Clone the repo

```bash
git clone https://github.com/your-username/mcp-email-tool.git
cd mcp-email-tool
```

### 2. Create and configure `.env`

Create a `.env` file in the project root with your SMTP settings:

```ini
SMTP_SERVER=smtp.yourprovider.com
SMTP_PORT=587
SMTP_USER=your_email@example.com
SMTP_PASS=your_email_password
```

### 3. Install dependencies

```bash
pip install fastmcp python-dotenv
```

### 4. Run the MCP server

```bash
python mcp_email_tool.py
```

By default, it starts at:

```
http://127.0.0.1:8004
```

---

## 🔌 Integration with Dify

This tool is designed to be used inside **Dify**:

1. Deploy the tool (make it accessible globally, e.g., with `ngrok`).
2. In your Dify instance, register it as an MCP tool by pointing to the endpoint.
3. Once registered, you can call the `send_email` function inside your Dify workflows.

---

## 🛠 Example Usage

Tool Function:

```python
@mcp.tool()
def send_email(subject: str, body: str, to_email: str) -> dict:
    """
    Send an email using SMTP.
    """
```

Expected call in Dify:

```json
{
  "tool": "send_email",
  "args": {
    "subject": "Test Email",
    "body": "Hello from Dify MCP!",
    "to_email": "recipient@example.com"
  }
}
```

Response:

```json
{
  "status": "success",
  "message": "Email sent!"
}
```

---

## 📌 Notes

* Make sure your SMTP provider allows external SMTP access.
* For Gmail, you may need to use **App Passwords** instead of your normal password.
* This tool is only a **backend utility**; it must be called from Dify or other MCP clients.

---
