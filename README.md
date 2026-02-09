# media-transform-platform

[![Frontend CI](https://github.com/obj809/frontend-media-transform-platform/actions/workflows/ci.yml/badge.svg)](https://github.com/obj809/frontend-media-transform-platform/actions/workflows/ci.yml)
[![Backend CI](https://github.com/obj809/backend-media-transform-platform/actions/workflows/ci.yml/badge.svg)](https://github.com/obj809/backend-media-transform-platform/actions/workflows/ci.yml)

- [https://github.com/obj809/frontend-media-transform-platform](https://github.com/obj809/frontend-media-transform-platform)
- [https://github.com/obj809/backend-media-transform-platform](https://github.com/obj809/backend-media-transform-platform)
- [https://github.com/obj809/db-media-transform-platform](https://github.com/obj809/db-media-transform-platform)
- [https://github.com/obj809/workers-media-transform-platform](https://github.com/obj809/workers-media-transform-platform)

Media Transform Platform is a set of focused repositories that together provide image upload, transformation, and delivery.

## Platform repositories

- `frontend-media-transform-platform`
  Next.js UI for file selection, upload, preview, and download.
- `backend-media-transform-platform`
  FastAPI service for health checks, upload validation, image processing, and file serving.
- `db-media-transform-platform`
  Database and persistence concerns for platform data.
- `workers-media-transform-platform`
  Worker processes for async/background media tasks.

## Local architecture

1. Frontend sends `GET /health` to verify backend connectivity.
2. Frontend uploads JPG files to `POST /upload`.
3. Backend stores upload in `uploads/`, processes image (grayscale), stores output in `processed/`.
4. Frontend previews/downloads via `GET /download/{filename}`.

## Prerequisites

- Node.js 20+
- Python 3.12+
- `npm` and `pip`

## Run locally

Start backend first, then frontend.

### Backend (`backend-media-transform-platform`)

```bash
python3 -m venv venv
source venv/bin/activate
pip install -r requirements.txt
uvicorn app.main:app --reload
```

Backend runs at `http://localhost:8000` (docs at `http://localhost:8000/docs`).

### Frontend (`frontend-media-transform-platform`)

```bash
npm install
npm run dev
```

Frontend runs at `http://localhost:3000`.

## Configuration

Frontend environment variable:

```bash
NEXT_PUBLIC_API_URL=http://localhost:8000
```

If unset, frontend defaults to `http://localhost:8000`.

## Backend API contract (current)

- `GET /`
  Returns a basic service message.
- `GET /health`
  Returns backend health status.
- `POST /upload`
  Accepts `image/jpeg` up to 25MB, returns stored and processed filenames with metadata.
- `GET /download/{filename}`
  Returns processed JPEG file by filename.

## Tests

### Frontend

```bash
npm test
```

### Backend

```bash
./venv/bin/python -m pytest -v
```

## CI

- Frontend CI runs lint, test, and build on push/PR to `main`.
- Backend CI runs pytest on push/PR to `main`.

## Troubleshooting

- Frontend shows backend offline:
  Confirm backend is running on `http://localhost:8000` or set `NEXT_PUBLIC_API_URL`.
- Upload fails:
  Ensure file is JPG/JPEG and under 25MB.
- Backend tests fail due to environment:
  Use the project venv interpreter (`./venv/bin/python -m pytest -v`).
