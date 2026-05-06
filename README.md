🔐 Secure Real-Time Chat
A full-stack, security-first communication platform with end-to-end encryption, JWT authentication, and an administrative oversight dashboard.

Python FastAPI Next.js TypeScript PostgreSQL MIT License

Features • Stack • Security • Setup • Structure

Overview
A high-performance, secure messaging platform designed with a security-first architecture. Built as part of a Secure Software Design and Engineering course, this project demonstrates real-world application of cryptographic principles, role-based access control, and secure API design in a full-stack environment.

The system provides real-time communication via WebSockets, encrypted data storage using Fernet symmetric encryption, and a dedicated admin dashboard for system monitoring — making it a practical reference for AppSec concepts applied in production-grade software.

✨ Features
Feature	Description
Real-Time Messaging	Bidirectional communication via WebSocket integration
Cryptographic Security	Fernet symmetric encryption for data at rest; message integrity validation
JWT Authentication	Stateless session management with role-based access control (RBAC)
Admin Dashboard	Room management, user oversight, and system log monitoring
Threat Modeling	Formal security documentation covering attack surfaces and risk management
Responsive UI	Mobile-ready interface built with Next.js 15 and Tailwind CSS
🛠 Tech Stack
Backend

Framework: Python + FastAPI (async-first REST + WebSocket API)
Database: PostgreSQL with SQLAlchemy ORM
Security Layer: Fernet symmetric encryption, JWT (PyJWT), Pydantic schema validation
Frontend

Framework: Next.js 15 (App Router)
Language: TypeScript
Styling: Tailwind CSS
Components: Radix UI / shadcn/ui (dialogs, avatars, tooltips)
🛡 Security Architecture
This system is designed around the principle of defense in depth:

┌─────────────────────────────────────────────────────┐
│                   CLIENT (Next.js)                  │
│           JWT stored securely · HTTPS/WSS           │
└──────────────────────┬──────────────────────────────┘
                       │ TLS in transit
┌──────────────────────▼──────────────────────────────┐
│                  API LAYER (FastAPI)                 │
│   JWT Auth Middleware · Pydantic Validation · RBAC  │
└──────────────────────┬──────────────────────────────┘
                       │
┌──────────────────────▼──────────────────────────────┐
│              DATA LAYER (PostgreSQL)                 │
│       Fernet-encrypted sensitive fields at rest      │
└─────────────────────────────────────────────────────┘
Data at Rest — Sensitive fields are encrypted with Fernet before database insertion.
Data in Transit — All traffic is intended to be served over TLS; WebSockets operate over wss://.
Authentication — JWT tokens with expiry enforce stateless, role-aware access.
Input Validation — Pydantic schemas sanitize and validate all incoming request data.
Threat Modeling — Project documentation includes a formal threat model with identified attack vectors and mitigations.

Prerequisites
Python 3.9+
Node.js 18+
A running PostgreSQL instance
Backend Setup
# 1. Navigate to the backend directory
cd Backend

# 2. Install Python dependencies
pip install -r requirements.txt

# 3. Create and populate your .env file
cp .env.example .env
# → Set DATABASE_URL, SECRET_KEY, FERNET_KEY

# 4. Start the FastAPI server
python main.py
The API will be available at http://localhost:8000. Interactive docs at /docs.

Frontend Setup
# 1. Navigate to the frontend directory
cd Frontend/real_chat_app

# 2. Install packages
npm install

# 3. Start the development server
npm run dev
The frontend will be available at http://localhost:3000.

📸 Screenshots
Admin Dashboard — room management, user monitoring, and system logs<img width="1904" height="831" alt="image" src="https://github.com/user-attachments/assets/a0949da4-fa16-4601-8af0-ad601883cbf7" />


imageimageimage
🔮 Roadmap
 End-to-end encryption (client-side key exchange)
 brute-force protection middleware
 Automated security testing with static and dynamic tools

