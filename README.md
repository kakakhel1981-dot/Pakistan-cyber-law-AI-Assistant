# Pakistan Cyber Law Assistant

A Streamlit app for general Pakistan cybercrime information, Q&A grounded in an uploaded PDF, and guidance for registering an online complaint.

## Features
- Professional Streamlit interface
- Groq-hosted chat model (configurable model ID)
- PDF text extraction and lightweight keyword retrieval
- Official FIA complaint portal link: https://complaint.fia.gov.pk/
- Complaint preparation checklist
- Legal disclaimer and privacy reminder

## Important model note
Groq API serves models hosted by Groq; it does **not** run OpenAI-hosted models. The starter default is `openai/gpt-oss-120b`, but model availability can change. Check Groq's current model list and replace `GROQ_MODEL` or the sidebar model ID with a model enabled for your account. If you specifically want an OpenAI model, use OpenAI's API and an OpenAI API key instead of Groq.

## Run locally
1. Install Python 3.10 or newer.
2. Create and activate a virtual environment (recommended).
3. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```
4. Copy `.streamlit/secrets.toml.example` to `.streamlit/secrets.toml`.
5. Put your Groq API key in the secrets file:
   ```toml
   GROQ_API_KEY = "gsk_your_key_here"
   ```
6. Start the app:
   ```bash
   streamlit run app.py
   ```

Never commit `.streamlit/secrets.toml` or expose your API key.

## Deploy on GitHub + Streamlit Community Cloud
1. Create a GitHub repository, e.g. `pakistan-cyber-law-assistant`.
2. Upload `app.py`, `requirements.txt`, `README.md`, `.gitignore`, and `.streamlit/secrets.toml.example`.
3. Open Streamlit Community Cloud and deploy the repository, selecting `app.py` as the main file.
4. In app settings → Secrets, add:
   ```toml
   GROQ_API_KEY = "gsk_your_key_here"
   GROQ_MODEL = "openai/gpt-oss-120b"
   ```
5. Redeploy/reboot the app if needed.

## PDF limitations
This version extracts selectable text from PDF pages. Scanned PDFs, screenshots, and images embedded in PDFs will not be understood by this starter version. Add OCR (for example, Tesseract) or a vision-capable PDF ingestion pipeline if you need image/screenshot understanding.

## Legal and privacy disclaimer
This is an educational/public-information tool, not a lawyer or official authority. It does not file complaints. Laws, agency responsibilities, and portal steps may change; verify current instructions through official sources. Avoid entering passwords, OTPs, CNIC details, intimate content, or other sensitive information unless absolutely necessary. Prompts are sent to Groq when using the API; check the provider's current data-handling terms.
