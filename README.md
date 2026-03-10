# MediScribe — Doctor Handwritten Prescription Detection System

> Mini Project | AI-Powered Medical Prescription Analysis using Claude Vision API

---

## 📌 Project Overview

MediScribe is a web application that uses Artificial Intelligence (Claude Vision API by Anthropic) to automatically read and extract information from handwritten doctor prescriptions. The user uploads a photo or scan of a prescription, and the system returns a structured breakdown including:

- Doctor's name, qualifications, clinic, and date
- Patient's name, age, gender, and contact
- List of medicines with dosage, frequency, duration, and instructions
- General instructions, diet advice, follow-up date, and warnings

---

## 🗂️ Project Structure

```
mediscribe/
├── app.py               ← Flask backend (main server file)
├── requirements.txt     ← Python dependencies
├── README.md            ← This file
└── templates/
    └── index.html       ← Frontend (HTML + CSS + JavaScript)
```

---

## ⚙️ Prerequisites

Make sure the following are installed on your system:

| Tool       | Version  | Download                        |
|------------|----------|---------------------------------|
| Python     | 3.9+     | https://www.python.org/downloads |
| pip        | Latest   | Comes with Python               |

---

## 🚀 Setup & Installation

### Step 1 — Clone / Download the project

Download and extract the project folder, or clone it:

```bash
git clone <repo-url>
cd mediscribe
```

### Step 2 — Install Python dependencies

```bash
pip install -r requirements.txt
```

This installs:
- **Flask** — the web framework
- **anthropic** — the official Anthropic Python SDK

### Step 3 — Add your API key

Open `app.py` and replace the placeholder on **line 20**:

```python
ANTHROPIC_API_KEY = "YOUR_API_KEY_HERE"
```

Replace with your actual Anthropic API key:

```python
ANTHROPIC_API_KEY = "sk-ant-api03-xxxxxxxxxxxxxxxxxx"
```

> 🔑 Get your API key from: https://console.anthropic.com

### Step 4 — Run the application

```bash
python app.py
```

You should see:

```
==================================================
  MediScribe - Prescription Detection System
  Running at: http://127.0.0.1:5000
==================================================
```

### Step 5 — Open in browser

Visit: **http://127.0.0.1:5000**

---

## 🧪 How to Use

1. Open the app in your browser
2. Click **"Drop prescription image here"** or drag and drop an image
3. Supported formats: **JPG, PNG, WEBP**
4. Click **"🔍 Analyze Prescription"**
5. Wait 5–15 seconds while the AI reads the prescription
6. View the extracted results on the right side

---

## 🛠️ Technology Stack

| Layer      | Technology              | Purpose                             |
|------------|-------------------------|-------------------------------------|
| Frontend   | HTML5, CSS3, JavaScript | User interface and image upload     |
| Backend    | Python 3 + Flask        | Web server and API handling         |
| AI Model   | Claude claude-opus-4-5 (Anthropic) | Handwriting recognition & extraction |
| API        | Anthropic Messages API  | Image understanding                 |

---

## 📂 File Descriptions

### `app.py`
The main Flask server. Key functions:
- `index()` — serves the homepage
- `analyze()` — receives uploaded image, sends to Claude, returns JSON
- `call_claude_vision()` — handles all communication with the Anthropic API
- `build_extraction_prompt()` — constructs the detailed AI prompt

### `templates/index.html`
Single-page frontend containing:
- Drag-and-drop image upload
- Image preview
- Results display with 4 sections (doctor, patient, medicines, instructions)
- Confidence indicator and readability notes

### `requirements.txt`
Lists all Python packages needed to run the project.

---

## 🐛 Troubleshooting

| Problem | Solution |
|--------|----------|
| `ModuleNotFoundError: flask` | Run `pip install -r requirements.txt` |
| `AuthenticationError` | Check your API key in `app.py` |
| `413 Request Entity Too Large` | Image too large — use a file under 10MB |
| Blank results returned | Try a clearer/higher resolution image |
| Port already in use | Change `port=5000` to `port=5001` in `app.py` |

---

## 📸 Sample Test

To test without a real prescription, use any clearly handwritten note with:
- A name and date at the top
- 2–3 lines with medicine names and doses
- Any instructions at the bottom

---

## 👨‍💻 Authors

Developed as a Mini Project submission.

---

## 📄 License

For academic use only. Not intended for real clinical diagnosis or prescription replacement.
