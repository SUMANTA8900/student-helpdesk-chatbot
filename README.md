i have some is it correct 
# Student Helpdesk Chatbot — Full Stack (React + Flask + Dataset)
👉 Problem: Students repeatedly ask the same queries (admissions, exams, campus info), overloading staff.

👉 Solution: AI-powered chatbot with FAQ + semantic search + GPT fallback, giving instant and reliable answers.

- **Frontend:** React + Vite + Tailwind
- **Backend:** Flask (Python), TF‑IDF FAQ retrieval
- **Dataset:** `backend/faq_dataset.json` (easy to edit/extend)

## 1) Quick Start

### Backend
```bash
cd backend
python -m venv .venv && source .venv/bin/activate  # (Windows: .venv\Scripts\activate)
pip install -r requirements.txt
# optional: copy .env
python app.py
```
Backend runs at **http://localhost:5000**.

### Frontend
```bash
cd frontend
# Node 18+ recommended
npm install
# optional: cp .env.example .env and set VITE_API_BASE if different
npm run dev
```
Open the printed local URL (usually `http://localhost:5173`).

## 2) How it works

- Frontend calls `POST /api/chat` with `{ message }`.
- Backend uses TF‑IDF + cosine similarity to find the closest question in the dataset.
- If similarity ≥ threshold (default 0.35), return the matched answer.
- Otherwise, return a helpful fallback response (you can wire an LLM here).

## 3) Customize the dataset
Edit `backend/faq_dataset.json`. Add items like:
```json
{ "question": "How do I apply for admissions?", "answer": "..." }
```
Restart backend to reload.

## 4) Optional: Adjust retrieval threshold
Set `SIMILARITY_THRESHOLD` in `backend/.env` (e.g., 0.25 for looser matching).

## 5) Deploy notes
- Enable CORS on backend (already included).
- For production:
  - Run `npm run build` inside `frontend/` → creates `dist/`.
  - Serve that `dist/` alongside backend, or host separately.
- Recommended: Deploy via **Google Cloud Run** using Docker (frontend + backend in one service).
- Don’t forget to set environment variables (`GROQ_API_KEY`, `SIMILARITY_THRESHOLD`, etc.).


👥 Team

Team Leader: Sumanta Singha (BWU/BTA/23/429)

Team Members:

    Tamanesh Das (BWU/BTA/23/479)

    Argha Dhang (BWU/BTA/23/477)

    Ayan Biswas (BWU/BTA/23/465)


👥 Team & Responsibilities

Team Leader: Sumanta Singha

Implemented core backend logic (TF-IDF, cosine similarity)

Designed backend API structure and integration with Flask

Worked on chatbot conversation flow

Tamanesh Das

Built the frontend UI using React + Tailwind

Integrated frontend with backend API endpoints

Assisted in frontend styling and responsive design

Argha Dhang

Coordinated the project workflow and deployment

Handled deployment on Google Cloud Run

Helped with testing across devices

Ayan Biswas

Managed dataset preparation and FAQ JSON structure

Documentation and dataset contribution

Conducted real-world survey and feedback collection
