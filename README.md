# Data Processing Engine

![frontend-ci](https://github.com/obj809/frontend-media-transform-platform/actions/workflows/ci.yml/badge.svg)
![backend-ci](https://github.com/obj809/backend-media-transform-platform/actions/workflows/ci.yml/badge.svg)

A full-stack image processing platform for uploading, transforming, and downloading images.

## Supported Formats

| Input | Output |
|-------|--------|
| JPG, PNG, HEIC/HEIF | JPG |

## Project Structure

| Repository | Description |
|------------|-------------|
| [Frontend](https://github.com/obj809/frontend-media-transform-platform) | Next.js web application |
| [Backend](https://github.com/obj809/backend-media-transform-platform) | FastAPI service |
<!-- | [Database](https://github.com/obj809/db-media-transform-platform) | Data layer |
| [Workers](https://github.com/obj809/workers-media-transform-platform) | Background processing | -->

## Tech Stack

**Frontend**: Next.js 16, React 19, TypeScript, Sass, Jest

**Backend**: Python 3.12+, FastAPI, Uvicorn, Pillow, pillow-heif, pytest

## Features

- Drag-and-drop file upload (anywhere on left section)
- Client-side validation (format and 25MB size limit)
- Backend health check with connection status indicator
- Image conversion to JPG
- Processed image preview and download

## API Endpoints

| Endpoint | Description |
|----------|-------------|
| `GET /` | Service info |
| `GET /health` | Health check |
| `POST /upload` | Upload and process image |
| `GET /download/{filename}` | Download processed image |

## Local Development

### Backend

```bash
cd backend-data-processing-engine
python3 -m venv venv
source venv/bin/activate
pip install -r requirements.txt
uvicorn app.main:app --reload
```

- API: http://localhost:8000
- Docs: http://localhost:8000/docs

### Frontend

```bash
cd frontend-data-processing-engine
npm install
npm run dev
```

- App: http://localhost:3000

Optional `.env.local`:
```bash
NEXT_PUBLIC_API_URL=http://localhost:8000
```

## Tests

```bash
# Frontend
cd frontend-data-processing-engine && npm test

# Backend
cd backend-data-processing-engine && ./venv/bin/pytest -v
```