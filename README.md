# 🔐 Secure Email Authentication Gateway

A Python-based email security application designed to inspect email authentication mechanisms and identify potential spoofing attempts. The gateway analyzes raw email headers, retrieves relevant DNS authentication records, and displays SPF, DKIM, and DMARC results through an interactive web dashboard.

## 🎯 Project Overview

Email spoofing and phishing attacks exploit weaknesses in sender authentication. This project demonstrates how three major email security standards work together to verify sender identity and improve email trust.

The application provides a centralized interface for examining authentication details and understanding whether an email passes the configured security checks.

## ✨ Key Capabilities

- **Email Header Inspection:** Extracts and processes information from raw email headers.
- **SPF Validation:** Identifies SPF authentication records through DNS queries.
- **DKIM Inspection:** Extracts DKIM signature parameters from email headers.
- **Public Key Retrieval:** Looks up DKIM public keys using DNS selectors and domains.
- **DMARC Evaluation:** Retrieves and interprets domain-level DMARC policies.
- **Security Dashboard:** Displays authentication outcomes in an organized format.
- **Practical Email Analysis:** Supports testing with original email headers.

## 🧩 System Workflow

The application follows a modular processing pipeline:

```text
       Raw Email Header
               |
               v
       Header Processing
               |
               v
      Authentication Engine
               |
       +-------+-------+
       |       |       |
       v       v       v
      SPF     DKIM    DMARC
       |       |       |
       +-------+-------+
               |
               v
        DNS Record Lookup
               |
               v
      Authentication Analysis
               |
               v
       Security Dashboard
```

## 🛠️ Technologies Used

| Technology | Purpose |
|---|---|
| Python | Core application development |
| Flask | Web application framework |
| dnspython | DNS record queries |
| dkimpy | DKIM signature processing |
| cryptography | Cryptographic key generation |
| HTML & CSS | User interface development |

## 📂 Repository Layout

```text
email-auth-gateway/
│
├── app.py
├── generate_dkim.py
├── requirements.txt
├── .env
├── .gitignore
├── README.md
│
├── auth/
│   ├── parser.py
│   ├── spf.py
│   ├── dkim.py
│   └── dmarc.py
│
├── keys/
│   ├── dkim_private.pem
│   └── dkim_public.pem
│
├── templates/
│   └── index.html
│
└── static/
    └── style.css
```

## 🚀 Installation and Execution

### Prerequisites
- Python 3.x
- pip package manager
- Internet connection for DNS lookups

### 1. Clone the repository

```bash
git clone https://github.com/ambp08/Secure-Email-Authentication-Gateway.git
cd Secure-Email-Authentication-Gateway
```

### 2. Set up a virtual environment

```bash
python -m venv venv
```

### 3. Activate the environment

**Windows PowerShell:**

```powershell
.\venv\Scripts\Activate.ps1
```

### 4. Install required packages

```bash
pip install -r requirements.txt
```

### 5. Generate DKIM key pair

```bash
python generate_dkim.py
```

### 6. Launch the application

```bash
python app.py
```

Access the application in your browser:

`http://127.0.0.1:5000`

## 🧪 How to Test

1. Open an email in Gmail.
2. Select **Show original** from the email options.
3. Copy the original email headers.
4. Paste them into the gateway.
5. Submit the headers for analysis.
6. Review the authentication results.

The dashboard reports the following authentication statuses:

| Protocol | Possible Results |
|---|---|
| SPF | PASS / FAIL / UNKNOWN |
| DKIM | PASS / FAIL / UNKNOWN |
| DMARC | PASS / FAIL / UNKNOWN |
