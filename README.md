# AI-Driven Email Assistant

An AI-powered email automation system that fetches, filters, summarizes, and generates responses to emails using advanced language models. It integrates with both IMAP and SMTP servers and utilizes a state-graph workflow to manage email processing.

## Table of Contents

- [Overview](#overview)
- [Features](#features)
- [Installation](#installation)
- [Configuration](#configuration)
- [Usage](#usage)
- [Directory Structure](#directory-structure)
- [Testing](#testing)
- [Contributing](#contributing)
- [License](#license)
- [Acknowledgments](#acknowledgments)

## Overview

This repository implements an email processing pipeline that leverages state-of-the-art language models (via Deepseek API) and a state graph workflow (using LangGraph) to:

- **Ingest Emails:** Fetch emails from an IMAP server or load simulated emails from a JSON file.
- **Filter Emails:** Classify incoming emails as _spam_, _urgent_, _informational_, or _needs review_.
- **Summarize Emails:** Generate concise summaries of email content.
- **Generate Responses:** Automatically draft email replies while allowing human review.
- **Send Emails:** Dispatch responses via SMTP or send drafts to a Gmail account.

## Features

- **Email Ingestion:** Supports both live email fetching (via IMAP) and simulation (via a local JSON file).
- **Filtering Agent:** Uses a language model to classify emails into categories.
- **Summarization Agent:** Generates 2–3 sentence summaries of email bodies.
- **Response Agent:** Drafts polite and professional responses based on email content and summaries.
- **Human Review:** Provides an option for manual review and editing of auto-generated responses.
- **State Graph Workflow:** Orchestrates the email processing steps (filtering, summarization, and response generation) with conditional transitions.
- **Logging:** Detailed logging for debugging and monitoring application behavior.

## Installation

### Prerequisites

- Python 3.8 or above
- [pip](https://pip.pypa.io/)
- (Optional) [virtualenv](https://virtualenv.pypa.io/)

### Setup

1. **Clone the repository:**

   ```bash
   git clone https://github.com/Ankitsingh0805/MailMind.git
   ```

2. **Create and activate a virtual environment (recommended):**

   ```bash
   python -m venv venv
   source venv/bin/activate  # On Windows: venv\Scripts\activate
   ```

3. **Install the dependencies:**

   ```bash
   pip install -r requirements.txt
   ```

## Configuration

The application requires several configuration settings (such as API keys and email server credentials). Create a `.env` file in the project root with the following variables:

```dotenv
# Deepseek API
DEEPSEEK_API_KEY=your_deepseek_api_key

# SMTP Settings
EMAIL_SERVER=smtp.yourserver.com
EMAIL_USERNAME=your_email@example.com
EMAIL_PASSWORD=your_email_password
EMAIL_PORT=587  # Or your SMTP port

# IMAP Settings (defaults to Gmail settings if not provided)
IMAP_USERNAME=your_imap_username
IMAP_PASSWORD=your_imap_password
IMAP_SERVER=imap.gmail.com
IMAP_PORT=993
```

Adjust the values as needed for your environment and email provider.

## Usage

To run the main email processing application, simply execute:

```bash
python main.py
```

### What to Expect

1. **Fetching Emails:**  
   The app will retrieve emails from your IMAP server (or simulate using `sample_emails.json` if configured for simulation).

2. **Email Processing:**  
   Each email is passed through a state graph workflow:
   - **Filtering:** Classifies the email (e.g., spam, urgent, informational, needs review).
   - **Summarization:** Generates a short summary of the email content.
   - **Response Generation:** Drafts a reply. If the response is uncertain or flagged for review, it prompts for human intervention.

3. **Sending/Drafting:**  
   You’ll be prompted to send the email or save it as a draft (which will be sent via SMTP to your specified Gmail address).



## Testing

To run tests (if provided), you can use a testing framework like `pytest`:

```bash
pytest
```

Or run:

```bash
python -m unittest discover
```

Ensure that any test dependencies are installed and that you have configured your environment variables for testing if needed.

## Contributing

Contributions are welcome! To contribute:

1. Fork the repository.
2. Create a new branch (`git checkout -b feature/my-feature`).
3. Commit your changes and push to your branch.
4. Open a Pull Request with a clear description of your changes.

Please follow our coding conventions and include relevant tests when applicable.



## Acknowledgments

- **Deepseek:** For the API and language model backend.
- **LangChain & LangGraph:** For the frameworks that help in building language model–driven workflows.
- **Open Source Contributors:** Thank you to everyone who has contributed to the libraries and tools used in this project.

---

This documentation should serve as a comprehensive guide to setting up, using, and contributing to the AI-Driven Email Assistant. Feel free to modify or expand sections as your project evolves.
