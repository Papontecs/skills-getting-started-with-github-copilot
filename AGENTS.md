# AGENTS.md

## Project overview

This repository is a small FastAPI learning app for Mergington High School. It serves a static web UI from `src/static` and exposes an in-memory activity signup API from `src/app.py`.

For the exercise context and product expectations, see:
- [README.md](README.md)
- [src/README.md](src/README.md)

## Repository layout

- [src/app.py](src/app.py): FastAPI app, in-memory activity data, and signup logic.
- [src/static/index.html](src/static/index.html): browser UI.
- [src/static/app.js](src/static/app.js): client-side behavior for the activity cards and signup workflow.
- [src/static/styles.css](src/static/styles.css): styling.
- [requirements.txt](requirements.txt): Python dependencies.
- [pytest.ini](pytest.ini): pytest configuration.

## Working conventions for AI agents

- Keep the app lightweight and Pythonic. This is a small service, not a large framework application.
- Prefer minimal, targeted edits in the existing structure instead of introducing extra layers or new frameworks.
- The app state is in memory only. Any seed data or signup state is lost when the server restarts.
- The static frontend is served at `/static` and the root route redirects to the HTML page. Changes in the UI and API should stay consistent with each other.
- If you add or change API behavior, update the related frontend logic or docs when needed.

## Common workflow

1. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```
2. Run the app locally:
   ```bash
   uvicorn src.app:app --reload --port 8000
   ```
3. Validate with tests when present:
   ```bash
   pytest
   ```
4. Open the app in a browser at:
   - http://localhost:8000/
   - http://localhost:8000/docs

## Important implementation notes

- The API is defined in `src/app.py`; the `activities` dictionary is the source of truth for available clubs and participants.
- Signups are currently validated only by whether the activity name exists and by appending the submitted email.
- Avoid introducing persistence, authentication, or a database unless the task explicitly asks for it.
- Keep route names and response shapes compatible with the current frontend expectations.

## Guidance for future customizations

- If you add new activity fields, keep them easy to render in the existing static frontend.
- If you write tests, focus on API behavior and the in-memory signup flow rather than browser automation.
- When adding new project instructions or skills, prefer small, repo-specific guidance over broad boilerplate.
