-# Retrieval-Augmented Clinical Symptom Intelligence Platform
-
-MedAssist AI is an end-to-end clinical decision-support prototype that leverages Retrieval-Augmented Generation (RAG) and large language models to analyze user-reported symptoms and generate structured, explainable outputs.
-
-It integrates FastAPI, Streamlit, OpenAI, and FAISS to simulate a modern AI-powered healthcare analytics system with FHIR-compatible outputs.
-
-🚀 **Key Features**
-🔍 Symptom Analysis with LLMs
-Uses OpenAI models to generate clinical insights from user input
-🧠 Retrieval-Augmented Generation (RAG)
-Enhances responses using external clinical knowledge (CDC/WHO docs)
-🏥 FHIR Output Generation
-Produces structured healthcare data using FHIR Observation resources
-📊 Query Logging
-Stores symptom queries and responses in PostgreSQL
-🌐 Full-Stack Architecture
-FastAPI backend
-Streamlit frontend
-Dockerized deployment
-⚡ Real-Time Interaction
-Instant analysis via API + UI integration
-
-
-🏗️ **Architecture**
-
-User (Streamlit UI)
-        ↓
-FastAPI Backend (/analyze)
-        ↓
-RAG Layer (FAISS + embeddings)
-        ↓
-OpenAI LLM (augmented prompt)
-        ↓
-FHIR Formatter + Database Logging
-        ↓
-Response → UI
-
-
-📁 **Project Structure**
-medassist-ai/
-│
-├── backend/
-│   ├── main.py
-│   ├── api/routes.py
-│   ├── services/
-│   │   ├── llm_service.py
-│   │   ├── rag_service.py
-│   │   ├── fhir_service.py
-│   ├── database/
-│   │   ├── db.py
-│   │   ├── models.py
-│   ├── config.py
-│   └── prompts.py
-│
-├── frontend/
-│   └── app.py
-│
-├── data/            # Clinical documents (CDC, WHO, etc.)
-├── embeddings/      # FAISS vector index
-│
-├── Dockerfile
-├── docker-compose.yml
-├── requirements.txt
-└── .env
+# MedAssist AI — Jupyter Notebook Setup
 
+This repo is now split into the required files to run the **main symptom-analysis flow** in Jupyter.
 
-⚙️ **Tech Stack**
-Backend: FastAPI, Uvicorn
-Frontend: Streamlit
-LLM: OpenAI API
-Vector DB: FAISS (via LangChain)
-Database: PostgreSQL + SQLAlchemy
-Healthcare Standard: FHIR (fhir.resources)
-Containerization: Docker
+## Included Components
 
+- `Dockerfile`
+- `docker-compose.yml`
+- `requirements.txt`
+- `.gitignore`
+- `MedAssistAI_Main.ipynb` (main runnable notebook)
+- `README.md`
 
-🔐 **Environment Variables**
-Create a .env file:
-OPENAI_API_KEY=your_api_key_here
-DATABASE_URL=postgresql://postgres:password@db:5432/medassist
+## Quick Start (Docker)
 
+1. Create `.env` in the project root:
 
-🧠 **How RAG Works**
-Clinical documents are embedded and stored in FAISS
-User symptom input is used to retrieve relevant context
-Context is injected into the LLM prompt
-The model generates a more accurate, grounded response
+```env
+OPENAI_API_KEY=your_openai_api_key_here
+```
 
+2. Build and start Jupyter:
 
+```bash
+docker compose up --build
+```
 
-▶️ **Running the Application**
-1. Start Backend (Docker)
-docker-compose up --build
-Backend runs at:
-http://localhost:8000
+3. Open in browser:
 
+- `http://localhost:8888`
 
-2. Start Frontend (Streamlit)
-cd frontend
-streamlit run app.py
-Frontend runs at:
-http://localhost:8501
+4. Run notebook:
 
+- Open `MedAssistAI_Main.ipynb`
+- Run cells top-to-bottom
 
-🔄 **API Endpoint**
-POST /analyze
-Request:
-{
-  "symptoms": "fever, cough, fatigue"
-}
-Response:
-{
-  "response": "...clinical analysis...",
-  "fhir": "{FHIR JSON}"
-}
+## Local Run (No Docker)
 
+```bash
+python -m venv .venv
+source .venv/bin/activate
+pip install -r requirements.txt
+jupyter notebook
+```
 
-🧪 **Test Workflow**
-Open Streamlit UI
+Then open `MedAssistAI_Main.ipynb`.
 
-Enter symptoms
+## What the Notebook Does
 
-Click Analyze
+- Loads `OPENAI_API_KEY` from `.env`
+- Initializes the OpenAI client
+- Defines `analyze_symptoms(symptoms: str)`
+- Executes a sample symptom analysis
 
-View:
-Clinical output
+## Important Note
 
-Risk interpretation
-
-Suggested codes
-
-FHIR JSON
-
-
-📦 **Docker Notes**
-Make sure your Dockerfile CMD is corrected:
-CMD ["uvicorn", "backend.main:app", "--host", "0.0.0.0", "--port", "8000"]
-
-
-⚠️ **Disclaimer**
-
-This project is for educational and demonstration purposes only.
-It is not a medical device and should not be used for diagnosis or treatment decisions.
-
-
-📈 **Future Improvements**
-
-🔬 Fine-tuned medical LLM integration
-
-📚 Expanded clinical knowledge base
-
-🧾 ICD-10 / SNOMED code mapping
-
-🔐 Authentication & HIPAA-compliant logging
-
-☁️ Cloud deployment (AWS/GCP/Azure)
-
-📊 Dashboard analytics (Power BI / Tableau integration)
-
-
-
-👨‍💻 **Author**
-Antoine Ward
-LinkedIn: https://linkedin.com/in/antoine-ward-mph-2401581a1
-GitHub: https://github.com/antoinewrd1
+This project is for educational use and is not a diagnostic medical tool.
 
EOF
)
