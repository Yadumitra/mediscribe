# MediScribe - Doctor Handwritten Prescription Detection System

Mini Project | AI-powered prescription extraction using Groq Vision

## Project Overview

MediScribe is a Flask web app that reads handwritten doctor prescriptions from an uploaded image and returns structured JSON output.

The app extracts:
- Doctor details (name, qualification, clinic, date, registration number)
- Patient details (name, age, gender, contact)
- Medicines (name, dosage, frequency, duration, route, notes)
- Instructions (general, diet, follow-up, warnings)
- Confidence level and readability notes

## Current Tech Stack

- Backend: Python + Flask
- Frontend: HTML, CSS, JavaScript (single template page)
- AI API: Groq Chat Completions with image input
- Model: `meta-llama/llama-4-scout-17b-16e-instruct`

## Project Structure

```text
rxreader_submission/
|- app.py
|- requirements.txt
|- README.md
|- templates/
|  |- index.html
```

## Requirements

- Python 3.9+
- pip

Install dependencies:

```bash
pip install -r requirements.txt
```

Current dependencies in `requirements.txt`:
- `flask==3.1.0`
- `groq==0.18.0`

## Configuration

In `app.py`, the Groq key is read from the constant:

```python
GROQ_API_KEY = "..."
```

The app initializes the client as:

```python
client = Groq(api_key=GROQ_API_KEY)
```

## Run the App

```bash
python app.py
```

Server starts at:
- `http://127.0.0.1:5000`

## How It Works

1. User uploads an image from the UI.
2. Frontend sends the file to `POST /analyze`.
3. Backend validates file extension and size.
4. Backend converts image bytes to base64 data URL.
5. Backend calls Groq with:
   - extraction prompt (`build_extraction_prompt()`)
   - image payload (`image_url`)
6. Model response is parsed as JSON and returned to frontend.
7. UI renders doctor, patient, medicines, instructions, confidence, and readability note.

## API Routes

- `GET /`
  - Serves `templates/index.html`

- `POST /analyze`
  - Accepts form field: `prescription` (image file)
  - Returns:
    - success response: `{ "success": true, "data": { ... } }`
    - error response: `{ "success": false, "error": "..." }`

## Accepted Upload Types and Limits

- Allowed types: `png`, `jpg`, `jpeg`, `webp`, `gif`
- Maximum upload size: 10 MB

## Frontend Features

- Drag-and-drop upload area
- Image preview before analysis
- Analyze button with loading spinner
- Section-wise output cards
- Confidence badge (high/medium/low)
- Readability notes for unclear handwriting

## Troubleshooting

- `ModuleNotFoundError`:
  - Run `pip install -r requirements.txt`

- Invalid file type error:
  - Upload image formats only (`jpg`, `png`, `webp`, `gif`)

- `413 Request Entity Too Large`:
  - Use image under 10 MB

- API/auth/model errors:
  - Verify `GROQ_API_KEY` and internet connectivity

- Port already in use:
  - Change `app.run(..., port=5000)` in `app.py`

## Notes

This project is for learning/academic use and is not a substitute for clinical judgment.
