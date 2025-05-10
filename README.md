# 📬 Gmail Spam Auto-Cleaner – Built with n8n

This project is a simple and effective automation built using [n8n](https://n8n.io).  
Its purpose is to automatically detect and delete spam or promotional emails from your Gmail inbox based on specific keywords — without writing any code.

---

## 🚀 Features

- Detects spammy or promotional keywords in incoming emails
- Automatically deletes those emails
- Runs fully automated in the background using n8n

---

## 🧰 Requirements

- A Gmail account with OAuth credentials set up in n8n
- n8n (self-hosted, cloud, or desktop app)
- Internet connection

---

## ⚙️ Workflow Overview

### 1. Gmail Trigger

- Node: **Gmail**
- Trigger type: `On message received`
- This triggers the workflow every time a new email arrives.

---

### 2. IF Node – Keyword Filter

- Node: **IF**
- Checks the `snippet` of the email (summary text)
- Logic: `{{$json["snippet"]}} contains [keyword]`
- Keywords used:
  - مجانًا (Free)
  - ربح (Win)
  - عرض خاص (Special offer)
  - خصم (Discount)
  - لا تفوت (Don't miss)
  - إشترك الآن (Subscribe now)
  - فرصة (Opportunity)
  - limited offer

Each condition is added under **OR**, meaning if any one of them is found, the condition passes.

---

### 3. Gmail – Delete Message

- Node: **Gmail**
- Action: `Delete a message`
- Message ID:  
