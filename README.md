# Retrieval-Augmented Clinical Symptom Intelligence Platform

MedAssist AI is an end-to-end clinical decision-support prototype that leverages Retrieval-Augmented Generation (RAG) and large language models to analyze user-reported symptoms and generate structured, explainable outputs.

It integrates FastAPI, Streamlit, OpenAI, and FAISS to simulate a modern AI-powered healthcare analytics system with FHIR-compatible outputs.

🚀 Key Features
🔍 Symptom Analysis with LLMs
Uses OpenAI models to generate clinical insights from user input
🧠 Retrieval-Augmented Generation (RAG)
Enhances responses using external clinical knowledge (CDC/WHO docs)
🏥 FHIR Output Generation
Produces structured healthcare data using FHIR Observation resources
📊 Query Logging
Stores symptom queries and responses in PostgreSQL
🌐 Full-Stack Architecture
FastAPI backend
Streamlit frontend
Dockerized deployment
⚡ Real-Time Interaction
Instant analysis via API + UI integration


🏗️ Architecture

User (Streamlit UI)
        ↓
FastAPI Backend (/analyze)
        ↓
RAG Layer (FAISS + embeddings)
        ↓
OpenAI LLM (augmented prompt)
        ↓
FHIR Formatter + Database Logging
        ↓
Response → UI


📁 Project Structure
medassist-ai/
│
├── backend/
│   ├── main.py
│   ├── api/routes.py
│   ├── services/
│   │   ├── llm_service.py
│   │   ├── rag_service.py
│   │   ├── fhir_service.py
│   ├── database/
│   │   ├── db.py
│   │   ├── models.py
│   ├── config.py
│   └── prompts.py
│
├── frontend/
│   └── app.py
│
├── data/            # Clinical documents (CDC, WHO, etc.)
├── embeddings/      # FAISS vector index
│
├── Dockerfile
├── docker-compose.yml
├── requirements.txt
└── .env


⚙️ Tech Stack
Backend: FastAPI, Uvicorn
Frontend: Streamlit
LLM: OpenAI API
Vector DB: FAISS (via LangChain)
Database: PostgreSQL + SQLAlchemy
Healthcare Standard: FHIR (fhir.resources)
Containerization: Docker


🔐 Environment Variables
Create a .env file:
OPENAI_API_KEY=your_api_key_here
DATABASE_URL=postgresql://postgres:password@db:5432/medassist


🧠 How RAG Works
Clinical documents are embedded and stored in FAISS
User symptom input is used to retrieve relevant context
Context is injected into the LLM prompt
The model generates a more accurate, grounded response



▶️ Running the Application
1. Start Backend (Docker)
docker-compose up --build
Backend runs at:
http://localhost:8000


2. Start Frontend (Streamlit)
cd frontend
streamlit run app.py
Frontend runs at:
http://localhost:8501


🔄 API Endpoint
POST /analyze
Request:
{
  "symptoms": "fever, cough, fatigue"
}
Response:
{
  "response": "...clinical analysis...",
  "fhir": "{FHIR JSON}"
}


🧪 Test Workflow
Open Streamlit UI

Enter symptoms

Click Analyze

View:
Clinical output

Risk interpretation

Suggested codes

FHIR JSON


📦 Docker Notes
Make sure your Dockerfile CMD is corrected:
CMD ["uvicorn", "backend.main:app", "--host", "0.0.0.0", "--port", "8000"]


⚠️ Disclaimer

This project is for educational and demonstration purposes only.
It is not a medical device and should not be used for diagnosis or treatment decisions.


📈 Future Improvements

🔬 Fine-tuned medical LLM integration

📚 Expanded clinical knowledge base

🧾 ICD-10 / SNOMED code mapping

🔐 Authentication & HIPAA-compliant logging

☁️ Cloud deployment (AWS/GCP/Azure)

📊 Dashboard analytics (Power BI / Tableau integration)

👨‍💻 Author


Antoine Ward
Healthcare Data Engineer | Data Scientist


LinkedIn: https://linkedin.com/in/antoine-ward-mph-2401581a1
GitHub: https://github.com/antoinewrd1
