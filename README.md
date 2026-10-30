# UK Day-Ahead Wind Forecast & Procurement Portal (`kjhwr`)

Web application built for a UK energy utility's Day-Ahead wholesale market trading team. It presents the latest available national wind generation forecasts (`WINDFOR`) prior to Day-Ahead market gate closure and quantitatively evaluates forecast error against actual wind generation (`FUELHH` - `WIND`) for purchase decisions made in **January 2026**.

## Live App 
- **Deployed Application (Vercel):** `https://ukwindproject.vercel.app/`

## AI Tools Disclosure
AI tools (Claude / Gemini / Cursor) were used to assist with boilerplate code generation, chart component styling, and documentation formatting. All domain logic, Elexon BMRS API integration, and quantitative accuracy metrics were reviewed and validated.

## Repository Structure
```text
kjhwr/
├── README.md                  # Project overview, architecture, and startup guide
├── docker-compose.yml         # Docker orchestration configuration
├── backend/
│   ├── Dockerfile             # Backend container specification
│   ├── requirements.txt       # Python dependencies (FastAPI, Uvicorn)
│   └── main.py                # FastAPI server: Elexon API fetch, D-1 alignment, error metrics
└── frontend/
    ├── Dockerfile             # Frontend container specification
    ├── package.json           # React, Vite, and Recharts dependencies
    ├── vite.config.js         # Vite configuration
    ├── index.html             # HTML entry point with Tailwind CSS
    └── src/
        ├── main.jsx           # React root mount
        └── App.jsx            # Main dashboard (Forecast View & Error Evaluation View)
```

## How to Start the Application (Local)

### 1. Start the Python Backend
```bash
cd backend
pip install -r requirements.txt
uvicorn main:app --reload --port 8000
```
The API will be available at `http://localhost:8000/api/dashboard`.

### 2. Start the React Frontend
Open a second terminal:
```bash
cd frontend
npm install
npm run dev
```
Open `http://localhost:5173` in your browser.

### Optional: Start via Docker
```bash
docker compose up --build
```
