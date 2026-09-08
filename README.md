# Sentiment Analysis of YouTube Comments

A small Flask web app that fetches YouTube comments for a video and performs basic sentiment analysis using TextBlob and NLTK.

## Features
- Fetches up to 100 comments from a YouTube video ID using the YouTube Data API
- Cleans text (lowercase, remove non-word chars, remove stopwords)
- Classifies each comment as Positive / Neutral / Negative using `TextBlob`
- Simple web UI served from `templates/index.html`

## Files
- `1.py` — Flask application and main entrypoint
- `sentiment.py` — (helper functions / alternate implementation)
- `s1.py` — (additional script)
- `templates/index.html` — front-end page
- `requirement.txt` — Python dependencies

## Prerequisites
- Python 3.8 or newer
- A Google YouTube Data API key (create one in Google Cloud Console)

## Install
1. Create and activate a virtual environment (recommended):

```bash
python -m venv venv
venv\Scripts\activate
```

2. Install dependencies:

```bash
pip install -r requirement.txt
```

3. (Optional) Pre-download NLTK stopwords to avoid the first-run download prompt:

```bash
python -m nltk.downloader stopwords
```

## Configuration
The app reads the YouTube Data API key from the environment variable `YOUTUBE_API_KEY`.
Create a local `.env` file (a template is included) or set the environment variable in your shell.

Example `.env` (copy `.env` and replace the value):

```text
YOUTUBE_API_KEY=REPLACE_WITH_YOUR_API_KEY
```

Set it in PowerShell for a single session:

```powershell
$env:YOUTUBE_API_KEY = 'YOUR_API_KEY_HERE'
```

Or in Command Prompt:

```cmd
set YOUTUBE_API_KEY=YOUR_API_KEY_HERE
```

Or in bash/macOS:

```bash
export YOUTUBE_API_KEY="YOUR_API_KEY_HERE"
```

## Run
Start the Flask app after setting `YOUTUBE_API_KEY`:

```bash
python 1.py
```

Open your browser at: http://127.0.0.1:5000

## Usage
1. Enter a YouTube video ID in the UI (for example: `dQw4w9WgXcQ`).
2. Click Analyze — the backend will fetch comments, clean them, and return sentiments.

The `/analyze` endpoint also returns JSON with cleaned `comments` and their `sentiments`.

## Notes
- The app sets `debug=True` when run directly; change this for production.
- You may need to install additional corpora for `TextBlob` depending on your environment.

## Contributing
Feel free to open issues or send pull requests. Small improvements:
- Move the API key into environment variables
- Add pagination to fetch more comments
- Add tests and CI

## License
This repository has no explicit license; add one if you plan to share publicly.
