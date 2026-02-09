# Media Transform Platform

![frontend-ci](https://github.com/obj809/frontend-media-transform-platform/actions/workflows/ci.yml/badge.svg)
![backend-ci](https://github.com/obj809/backend-media-transform-platform/actions/workflows/ci.yml/badge.svg)

## Project Overview
Media Transform Platform is a full-stack application for image upload, transformation, and delivery.

## Project Links

- [Frontend](https://github.com/obj809/frontend-media-transform-platform)
- [Backend](https://github.com/obj809/backend-media-transform-platform)
- [Database](https://github.com/obj809/db-media-transform-platform)
- [Workers](https://github.com/obj809/workers-media-transform-platform)

# Frontend - Next.js Application

https://github.com/obj809/frontend-media-transform-platform

## Tech Stack

Next.js 16, React 19, TypeScript, Sass, Tailwind CSS 4, Jest, Testing Library, ESLint

## Project Features

- [x] Drag-and-drop JPG upload flow
- [x] Client-side validation (JPG/JPEG, 25MB max)
- [x] Backend health check integration
- [x] Processed image preview and download action
- [x] CI lint, test, and build pipeline

# Backend - FastAPI API

https://github.com/obj809/backend-media-transform-platform

## Tech Stack

Python 3.12+, FastAPI, Uvicorn, Pillow, pytest, GitHub Actions

## Project Features

- [x] `GET /` and `GET /health` service endpoints
- [x] `POST /upload` with content-type and size validation
- [x] Image processing pipeline (grayscale transform)
- [x] `GET /download/{filename}` for processed media delivery
- [x] Automated API and upload tests in CI

# Database - Platform Data Layer

https://github.com/obj809/db-media-transform-platform

## Focus

- [x] Platform data modeling and persistence
- [x] Schema and storage support for media metadata
- [x] Backend-aligned data contracts

# Workers - Background Processing

https://github.com/obj809/workers-media-transform-platform

## Focus

- [x] Asynchronous media processing tasks
- [x] Background job orchestration
- [x] Scalable worker execution patterns

# Local Development

Start backend first, then frontend.

## Backend

```bash
python3 -m venv venv
source venv/bin/activate
pip install -r requirements.txt
uvicorn app.main:app --reload
```

Backend URL: `http://localhost:8000`  
API docs: `http://localhost:8000/docs`

## Frontend

```bash
npm install
npm run dev
```

Frontend URL: `http://localhost:3000`

Frontend environment variable:

```bash
NEXT_PUBLIC_API_URL=http://localhost:8000
```

# Backend API Endpoints

- `GET /`
- `GET /health`
- `POST /upload`
- `GET /download/{filename}`

# Test Commands

## Frontend

```bash
npm test
```

## Backend

```bash
./venv/bin/python -m pytest -v
```
