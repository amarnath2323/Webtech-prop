# Resume Portfolio Builder Pro (Frontend MVP)

A responsive browser-based career workspace built with HTML, CSS, and vanilla JavaScript.

## Features

- Resume editor with personal details, education, internship, skills, certifications, and project sections
- Live resume preview with three visual templates
- Browser print dialog for saving the resume as PDF
- Portfolio preview with three themes and downloadable standalone HTML
- Local job-description keyword coverage analyzer
- Job application tracker with statuses and notes
- Local writing-assistant demo for summaries, bullet points, projects, skills, and cover letter introductions
- Dashboard profile completeness and summary statistics
- Browser-local persistence, JSON backup export/import, dark mode, and responsive layouts

## Run locally

### Option 1: VS Code Live Server

1. Extract the ZIP.
2. Open the `resume-portfolio-builder-pro` folder in VS Code.
3. Install the **Live Server** extension if you do not have it.
4. Right-click `index.html` and choose **Open with Live Server**.

### Option 2: Python's built-in static server

Open a terminal in this folder and run:

```bash
python -m http.server 8000
```

Then open `http://localhost:8000`.

You can also open `index.html` directly, but using a local server is recommended for clipboard and browser behavior.

## Important MVP limitations

- Data is stored in `localStorage` on the current browser and device. There is no user authentication, cloud sync, or server database.
- The AI assistant uses local demo suggestions. It does not call a real AI model.
- The ATS analyzer is a simple keyword-overlap heuristic, not a real ATS score or hiring prediction.
- Resume PDF export uses the browser print dialog. Select **Save as PDF** and choose A4 paper if needed.
- The portfolio download creates a standalone HTML file; it does not publish it online automatically.

## Safe path to real AI

Do not put a secret API key in `app.js`, HTML, or any frontend environment variable bundled into the browser. Add a backend endpoint such as `POST /api/ai/suggest` using a server-side environment variable for the provider key. The browser should call that endpoint, and the server should validate input, enforce limits, and call the AI provider.

## Suggested next-stage architecture

```text
Frontend (this project)
  ├── Resume editor and live preview
  ├── Portfolio generator
  ├── ATS analyzer and job tracker
  └── fetch('/api/...')
          |
Backend API (next stage: Flask or Spring Boot)
  ├── Authentication and authorization
  ├── Resume and project CRUD
  ├── AI provider proxy (server-side API key)
  └── Validation and rate limits
          |
Database (next stage: MySQL or PostgreSQL)
  ├── users
  ├── user_profiles
  ├── resumes
  ├── resume_sections
  ├── projects
  ├── job_applications
  └── ai_usage_logs (optional, avoid storing unnecessary personal text)
```

## Deploy online

This is a static site and can be hosted on GitHub Pages, Netlify, or Vercel. Upload the three frontend files (`index.html`, `styles.css`, and `app.js`) plus this README. Any saved data remains in each visitor's browser. A deployed static site alone cannot safely protect a private AI key or provide cloud accounts/database features.

## Suggested database schema for a later backend

See `schema.sql`. It is a starting point for the backend stage; the frontend MVP does not connect to it.
