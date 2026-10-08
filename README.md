# Legal AI Assistant (Indian Legal Document Analysis & Case Research Platform)

An educational and legal research platform for Indian jurisprudence, statutory analysis, contract risk review, and source-grounded RAG assistance.

---

## ⚖️ Ethical Safeguards & Educational Boundaries
1. **Academic & Research Only**: This platform is designed exclusively for educational and academic legal research.
2. **No Legal Advice**: It must never be used to provide formal legal advice, claim guaranteed case outcomes, or establish legal rights.
3. **Source-Grounded RAG**: All research answers explicitly cite their source document page, paragraph, and chunk offsets. Queries lacking sufficient textual support are safely declined.
4. **Experimental Outcome Analysis**: Labelled strictly as *"Experimental historical-pattern analysis"* with explicit calibration and uncertainty indicators.

---

## 🏛️ System Architecture & Features

```
legal-ai-assistant/
  ├── frontend/         # Next.js 14, React, TypeScript, Tailwind CSS, 3-Pane Document Studio
  ├── backend/          # Python FastAPI, SQLAlchemy 2.0, Alembic, Celery, Redis, pgvector
  ├── ml/               # TF-IDF + SVM, Hybrid Legal NER, Clause Detectors, Model Cards
  ├── infrastructure/   # PostgreSQL + pgvector init scripts, Redis, MinIO
  ├── sample_data/      # Curated Indian Supreme Court judgments, IPC, Constitution, Contracts
  ├── docker-compose.yml
  └── README.md
```

### Key Capabilities
- **Document Ingestion**: PDF (with OCR fallback), DOCX, and TXT parsing with page/paragraph position preservation.
- **Classification**: 9 Document Types & 11 Case Categories (TF-IDF + Linear SVM baseline & Legal-BERT interfaces).
- **Hybrid Legal NER**: Extraction of 14 entity types (*Judges, Advocates, Petitioners, Respondents, Courts, Acts, Sections, Articles, Case Numbers, etc.*).
- **Indian Acts & Section Detector**: Canonical normalization for IPC, CrPC, HMA, Contract Act, Arbitration Act, and Constitutional Articles.
- **Contract Clause & Risk Review Checklist**: 15 commercial clause types with transparent drafting review flags.
- **Hybrid Legal Search**: PostgreSQL Full-Text Search (BM25) combined with pgvector dense cosine similarity.
- **Source-Grounded RAG Assistant**: Interactive cited Q&A engine.

---

## 🚀 Quick Start (Local Setup)

### Option 1: Using Docker Compose (Recommended)

1. **Clone and Configure Environment**:
   ```bash
   cp .env.example .env
   ```

2. **Start All Services**:
   ```bash
   docker-compose up -d --build
   ```

3. **Seed Database with Indian Legal Sample Data**:
   ```bash
   docker-compose exec backend python ../sample_data/seed_database.py
   ```

4. **Access the Applications**:
   - **Frontend UI**: [http://localhost:3000](http://localhost:3000)
   - **FastAPI Interactive Swagger Docs**: [http://localhost:8000/docs](http://localhost:8000/docs)
   - **MinIO Console**: [http://localhost:9001](http://localhost:9001)

---

### Option 2: Running Directly on Host (Python & Node.js)

#### 1. Backend Setup:
```bash
cd backend
python3 -m venv venv
source venv/bin/activate
pip install -r requirements.txt

# Start Backend Server
uvicorn app.main:app --host 0.0.0.0 --port 8000 --reload
```

#### 2. Frontend Setup:
```bash
cd frontend
npm install
npm run dev
```

---

## 🔑 Demo Login Accounts

| Role | Email | Password | Permissions |
|---|---|---|---|
| **Student / Researcher** | `student@legalai.edu` | `student123` | Upload docs, hybrid search, RAG chat, case similarity |
| **Faculty / Reviewer** | `faculty@legalai.edu` | `faculty123` | All researcher tools + entity & classification corrections |
| **Administrator** | `admin@legalai.edu` | `admin123` | System-wide audit logs, model cards, evaluation metrics |

---

## 🧪 Running Automated Tests

Run the full pytest suite for auth, workspace RBAC, parser, classifier, NER, Acts normalization, and clause risk engines:

```bash
cd backend
pytest -v
```

---

## 📄 License & Attribution
- Built for educational and academic research in Indian Law & Artificial Intelligence.
- Open-source under the MIT License.
