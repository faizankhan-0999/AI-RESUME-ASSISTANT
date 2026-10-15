# AI-RESUME-ASSISTANT# 📄 AI Resume ATS Checker

A Streamlit app that scores a resume for ATS (Applicant Tracking System) compatibility and gives specific, actionable improvements using Google's Gemini Flash model.

## Features

- Upload a resume as **PDF, DOCX or TXT**
- Overall **ATS score (0–100)** with a 5-category breakdown:
  Keywords & Relevance, Formatting & Structure, Impact & Achievements, Clarity & Grammar, Contact & Completeness
- Optional **job description** input for role-specific keyword matching
- Prioritized **improvement suggestions**, missing keywords, strengths and **bullet-point rewrites**

## Project structure

```
.
├── app.py
├── requirements.txt
└── README.md
```

## Run locally

1. **Get a free Gemini API key** at https://aistudio.google.com/apikey

2. **Clone the repo and install dependencies** (Python 3.9+):

   ```bash
   git clone https://github.com/<your-username>/<your-repo>.git
   cd <your-repo>
   python -m venv venv
   source venv/bin/activate        # Windows: venv\Scripts\activate
   pip install -r requirements.txt
   ```

3. **Provide your API key** (pick one):

   - Environment variable:
     ```bash
     export GEMINI_API_KEY="your-key"      # Windows PowerShell: $env:GEMINI_API_KEY="your-key"
     ```
   - Or create `.streamlit/secrets.toml`:
     ```toml
     GEMINI_API_KEY = "your-key"
     ```
   - Or just paste it into the sidebar when the app runs.

4. **Start the app:**

   ```bash
   streamlit run app.py
   ```

## Deploy on Streamlit Community Cloud

1. Push this project to a GitHub repository.
2. Go to https://share.streamlit.io and sign in with GitHub.
3. Click **Create app** → select your repo, branch `main`, and main file `app.py`.
4. Open **Advanced settings → Secrets** and add:
   ```toml
   GEMINI_API_KEY = "your-key"
   ```
5. Click **Deploy**.

> ⚠️ Never commit your API key. Add `.streamlit/secrets.toml` to `.gitignore`.

## Configuration

The model name defaults to `gemini-3.8-flash` and can be changed in the sidebar (or edit `DEFAULT_MODEL` in `app.py`). If you get a "model not found" error, check the current list of model IDs at https://ai.google.dev/gemini-api/docs/models — for example `gemini-3.5-flash-lite` is a cheaper alternative.

## Notes

- Scanned/image-only PDFs have no extractable text. If the app can't read your resume, an ATS likely can't either — export a text-based PDF or use DOCX.
- Resume text is sent to the Gemini API for analysis. The app itself doesn't store it.
- The score is an AI estimate, not an official score from any specific ATS.

## License

MIT
