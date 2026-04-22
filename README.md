# RAHI (Rural AI Healthcare Interface)

## 🌍 Overview
**RAHI** (Rural AI Healthcare Interface) is a comprehensive, full-stack hybrid healthcare ecosystem specifically designed to address the healthcare challenges in rural India. It bridges the gap between rural patients and urban medical professionals by leveraging low-connectivity optimizations, artificial intelligence for triage, and extensive multilingual support. 

## 🚀 Key Features
- **AI-Powered Triage:** A Random Forest-based AI engine that predicts diseases based on symptoms to assist doctors in preliminary diagnosis.
- **Multilingual Support:** Localized interface (via i18n) to cater to diverse linguistic demographics in rural areas.
- **Low-Connectivity Resilience:** Offline storage and background synchronization using SMS/USSD fallbacks for areas with poor internet connectivity.
- **Role-Based Access Control (RBAC):** Secure access for Doctors, Patients, and Admins.
- **Hybrid Infrastructure:** A unified monorepo encompassing a web-based Doctor Dashboard and an Expo-based Mobile Patient App.

## 🏗 System Architecture (Monorepo)

| Scope | Service | Technology Stack | Location |
| :--- | :--- | :--- | :--- |
| **Frontend** | Doctor Dashboard | Next.js (React), Tailwind CSS | `apps/web` |
| **Frontend** | Patient App | React Native (Expo) | `apps/mobile` |
| **Backend API** | Core Services | FastAPI (Python), JWT Auth | `backend` |
| **AI Service** | Disease Prediction | Scikit-Learn, FastAPI | `ai-engine` |
| **Database** | Relational & NoSQL | PostgreSQL, MongoDB | `infrastructure/` |
| **Infrastructure** | Orchestration | Docker, Nginx, Redis | `infrastructure/` |

## 🛠️ Tech Stack
- **Frontend:** Next.js 14, React Native (Expo), Tailwind CSS, Framer Motion
- **Backend:** Python 3.10+, FastAPI, SQLAlchemy, Beanie (MongoDB)
- **AI & Machine Learning:** Scikit-Learn, Pandas, NumPy
- **Databases:** PostgreSQL (Relational Data), MongoDB (Unstructured Data/Logs), Redis (Caching)
- **DevOps & Deployment:** Docker, Docker Compose, Nginx, GitHub Actions

## ⚙️ Quick Start

### 1. Prerequisites
- **Docker Desktop** (Make sure the Docker daemon is running)
- **Node.js** (v18+) 
- **Python** (v3.10+)
- **Make** (Optional, but recommended)

### 2. Running with Docker (Recommended)
The easiest way to start the entire ecosystem (Backend, AI Engine, Web App, Mobile App, Databases) is via Docker.

```bash
# Clone the repository
git clone https://github.com/ABDUL223344/RAHI.git
cd RAHI

# Start all services
make up
# Or if you're on Windows without Make:
docker-compose up --build -d
```

### 3. Manual Development Setup

If you prefer running the services locally for development:

**Backend (FastAPI):**
```bash
cd backend
python -m venv venv
# Windows: venv\Scripts\activate | Mac/Linux: source venv/bin/activate
pip install -r requirements.txt
uvicorn main:app --reload --port 8000
```

**AI Engine:**
```bash
cd ai-engine
python -m venv venv
# Activate venv
pip install -r requirements.txt
uvicorn main:app --reload --port 8001
```

**Web Dashboard (Next.js):**
```bash
cd apps/web
npm install
npm run dev
```

**Mobile App (Expo):**
```bash
cd apps/mobile
npm install
npx expo start
```

## 🔐 Security & QA
- **Authentication:** JWT-based secure login with Role-Based Access Control (RBAC).
- **Hardened Security:** `CORSMiddleware`, `TrustedHostMiddleware`, and rate limiting configured.
- **Testing:** Comprehensive test suite included for Backend (`tests/test_api.py`) and AI Engine (`tests/test_model.py`). Use `locustfile.py` for load testing.

## 📦 Production Deployment
For production, the infrastructure uses Nginx as a reverse proxy, and Docker restart policies.
```bash
# Deploy using the production docker-compose file
docker-compose -f docker-compose.prod.yml up --build -d
```
There is also a `deploy.sh` script included for automated CI/CD processes.

## 📄 License
This project is licensed under the MIT License.
