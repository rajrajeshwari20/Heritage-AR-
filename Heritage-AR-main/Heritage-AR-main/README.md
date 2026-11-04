# Heritage-AR

AR-powered heritage tourism platform built with Flask.

## Run locally on Windows

From the project directory (the folder containing `run.py`), create a virtual environment and install the development dependencies:

```powershell
py -3.11 -m venv .venv
.\.venv\Scripts\Activate.ps1
python -m pip install --upgrade pip
python -m pip install -r requirements-dev.txt
python run.py
```

Open [http://127.0.0.1:5000/](http://127.0.0.1:5000/).

If PowerShell prevents environment activation, run the commands directly through the virtual environment instead:

```powershell
.\.venv\Scripts\python.exe -m pip install -r requirements-dev.txt
.\.venv\Scripts\python.exe run.py
```

For a runtime-only install, use `requirements.txt` instead of `requirements-dev.txt`.

## Optional integrations

The site and its local heritage knowledge fallback work without external service credentials.

- **Firebase authentication:** Login and registration require a Firebase project with Email/Password authentication enabled. Copy `.env.example` to `.env`, set `FIREBASE_API_KEY`, and provide a Firebase service-account JSON file using `FIREBASE_CREDENTIALS` (or place it at the project root as `firebase-service-account.json`). Never commit the service-account file or share its private key.
- **Generated AI answers:** HeritageAI uses Ollama when it is running locally. Install Ollama, then run `ollama pull qwen2.5:0.5b`. Set `OLLAMA_HOST` or `OLLAMA_MODEL` in `.env` only if using a non-default host or model. Without Ollama, the assistant falls back to answers extracted from the local heritage knowledge base.

## Tests

Run the application test suite with:

```powershell
.\.venv\Scripts\python.exe -m pytest tests -q
```
