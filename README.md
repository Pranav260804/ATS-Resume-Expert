# ATS Resume Tracker

## Overview

The **ATS Resume Tracker** is a full-stack web application that provides a comprehensive, AI-powered analysis of resumes against specific job descriptions (JDs). It utilizes **Google Gemini API** for contextual understanding, **LangChain** for orchestration, and **MongoDB** with vector search to implement **Retrieval-Augmented Generation (RAG)**. This ensures deep semantic matching between resumes and job descriptions.

The system offers a professional evaluation of uploaded PDF resumes, computes a **percentage match**, generates a **strengths and weaknesses analysis**, and enhances accessibility with **audio playback** and **YouTube video generation**. The results can be **viewed on the site**, **emailed to the user**, or **downloaded as a PDF report**.

---

### Project Demonstration:

https://github.com/user-attachments/assets/ece1e23b-7785-49ea-9d80-0421828c10e6

### Application Interface:

**Lgin and Registeration**
![login](https://github.com/user-attachments/assets/016528ab-07ab-49a6-af0e-a8623aa49efb)

**Upload and Analyze Resume:**

![Web Interface](https://github.com/user-attachments/assets/d9d2b6cd-e140-4304-ae23-35d948a800c8)

**Evaluation Result Page:**

![Result Page](https://github.com/user-attachments/assets/bd5a4c70-0fef-4fb4-a6f7-c2dae2df9bc3)

**Emailed Report Screenshot:**

![Email Result](https://github.com/user-attachments/assets/03a4dab1-f217-41f9-b21d-6b5df6527653)

**Youtube vedio recommendation:**
![yt](https://github.com/user-attachments/assets/5148987d-971a-484f-a3be-56d8844da8bd)

## Project Features

- **Resume Upload and Parsing**: Accepts resumes in PDF format and extracts structured content such as skills, education, experience, etc.
- **Contextual JD Matching**: Uses **LangChain + Gemini API + MongoDB vector index** to retrieve and compare relevant information from the resume and job description.
- **Strengths and Weaknesses Evaluation**: AI-generated summary that highlights what a candidate excels in and areas needing improvement.
- **Percentage Match Score**: Reflects how closely the resume aligns with the job description based on AI-driven semantic similarity.
- **Audio Playback**: The result section includes a "Play Audio" button that reads the summary aloud using text-to-speech.
- **PDF Download**: The complete evaluation can be downloaded by the user as a professionally formatted PDF.
- **YouTube Integration**: Based on the evaluation, the app uses the **YouTube API** to recommend personalized videos (e.g., resume tips, upskilling tutorials) directly within the UI.
- **Email Notification**: The final result is emailed to the user for easy reference.
- **Modern Web Interface**: Built using Flask, HTML, CSS, and JavaScript to ensure responsive and user-friendly design.

---

## Tech Stack

| Layer                | Technology                                                                                      |
| -------------------- | ----------------------------------------------------------------------------------------------- |
| **Backend**          | Python, Flask                                                                                   |
| **Frontend**         | HTML, CSS, JavaScript                                                                           |
| **Gen AI model**           | Gemini 2.5 Flash (Google Generative AI) for reasoning & generation; LangChain for orchestration |
| **Embeddings**       | text-embedding-004 (Google Generative AI) for vector representation                             |
| **Database**         | MongoDB Atlas with vector search                                                                |
| **Audio**            | Client-side audio playback using the Web Speech API (`SpeechSynthesisUtterance`)                |
| **Video Suggestion** | YouTube Data API                                                                                |
| **Email Delivery**   | SMTP (Gmail)                                                                                    |
| **PDF Generation**   | Built-in browser print dialog via JavaScript’s `window.print()`                                 |


## Prerequisites

- Python 3.x
- MongoDB Atlas account with vector indexing enabled
- Gemini API access (Google Generative AI)
- Gmail account with app password (for SMTP)
- YouTube API key

---

## Repository Setup

### Clone the Repository

```bash
git clone https://github.com/sahilchalke0001/resume
cd resume
```

### Create a Virtual Environment

```bash
python -m venv venv
source venv/bin/activate  # Windows: venv\Scripts\activate
```

### Install Dependencies

```bash
pip install -r requirements.txt
```

### Environment Configuration

Create a `.env` file in the root directory and add the following keys:

```env
FLASK_SECRET_KEY=4ddcdd430dc9d6f3848cc171d0c54358f2aa9e3f2a8fcc27167353105a4b610d

# Google Generative AI / Gemini API
GEMINI_API_KEY=your_api_key_here
GOOGLE_API_KEY=your_google_api_key_here

# Gmail for SMTP
SENDER_EMAIL=your_email@gmail.com
EMAIL_PASSWORD=your_gmail_app_password

# YouTube API (for video suggestions)
YOUTUBE_API_KEY=your_youtube_api_key

# MongoDB RAG Setup
MONGO_URI=mongodb+srv://<username>:<password>@cluster0.mongodb.net/db?retryWrites=true&w=majority&appName=Cluster0
MONGO_DB_NAME=db
MONGO_KB_COLLECTION=knowledge_chunks
MONGO_VECTOR_INDEX=default
```

---

## Running the Application

```bash
python app.py
```

Then visit:

```
http://127.0.0.1:5000/
```

---

## How to Use

1. Open the web interface and upload your resume in PDF format.
2. Paste or write your target job description.
3. Click the **Analyze** button.
4. The application will:

   - Parse the resume
   - Contextually match it with the job description using RAG
   - Generate a percentage match
   - Summarize key strengths and weaknesses
   - Provide video suggestions
   - Offer audio narration of the result
   - Allow download of the PDF
   - Email the complete report

---


## License

This project is licensed under the **MIT License**.

---

## Contact

For queries, feedback, or collaboration opportunities, please contact:
**[kalepranav2608@gmail.com](mailto:kalepranav2608@gmail.com)**

---
![Python](https://img.shields.io/badge/Python-3.x-blue)
![Flask](https://img.shields.io/badge/Framework-Flask-green)
![MongoDB](https://img.shields.io/badge/Database-MongoDB%20Atlas-brightgreen)
![Gemini AI](https://img.shields.io/badge/LLM-Google%20Gemini-orange)
![LangChain](https://img.shields.io/badge/Orchestration-LangChain-yellow)
![License](https://img.shields.io/badge/License-MIT-lightgrey)

**AI-powered ATS Resume Analyzer using Retrieval-Augmented Generation (RAG), Gemini API, and MongoDB Vector Search.**

---

## System Architecture

The ATS Resume Tracker follows a **Retrieval-Augmented Generation (RAG)** architecture:

1. User uploads a resume and provides a job description.
2. The resume is parsed and converted into structured text.
3. Text is embedded using **Google Generative AI embeddings**.
4. Embeddings are stored in **MongoDB Atlas Vector Search**.
5. LangChain retrieves relevant chunks from the vector database.
6. Gemini API performs semantic comparison with the job description.
7. The system generates:

   * Match percentage
   * Strengths & weaknesses
   * Recommendations
8. The result is displayed in the UI, converted to speech, and optionally emailed or downloaded.

---

## Project Structure

```
resume/
│
├── app.py                    # Main Flask application
├── requirements.txt          # Python dependencies
├── .env                      # Environment variables
│
├── templates/                # HTML templates
│   ├── login.html
│   ├── register.html
│   ├── upload.html
│   └── result.html
│
├── static/                   # CSS, JS, images
│
├── utils/                    # Helper modules
│   ├── resume_parser.py
│   ├── rag_engine.py
│   ├── email_service.py
│   └── youtube_recommender.py
│
└── README.md
```

---

## Example Output

**Match Score:** 82%

**Strengths:**

* Strong Python and Machine Learning background
* Experience with REST APIs and cloud services
* Demonstrated project work in AI/ML

**Weaknesses:**

* Limited experience with large-scale production systems
* Missing some required DevOps skills such as Docker/Kubernetes

---

## Future Improvements

* Multi-resume batch analysis
* Integration with LinkedIn job postings
* Real-time ATS scoring dashboard
* Resume rewriting suggestions using LLMs
* Support for DOCX and TXT resume formats
* Candidate skill-gap learning roadmap

---

## 🌐 AI Platform (In Development)

We are currently building an **AI-focused platform and portfolio hub** that showcases advanced projects in **Artificial Intelligence, Machine Learning, and Generative AI systems**.

This platform will include:

* AI project demonstrations
* Interactive system architectures
* Research-based implementations
* Developer portfolio integration

The ATS Resume Tracker will be integrated as one of the **core AI applications** within this platform.

---

## 📬 Contact

For queries, feedback, or collaboration opportunities:

📧 **Email:** [kalepranav2608@gmail.com](mailto:kalepranav2608@gmail.com)

💼 **LinkedIn:**
(Add your LinkedIn profile link here)

🌐 **AI Portfolio Website:**
(Add your AI portfolio website link here)

---

## ⭐ Support the Project

If you found this project useful, please consider giving it a **star on GitHub**.
It helps the project gain visibility and motivates further development.
