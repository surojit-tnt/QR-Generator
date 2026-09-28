

# Text to QR Generator

A simple web app that turns text or a URL into a QR code. The frontend is built with React, and the API is powered by FastAPI.

## Features

- Enter text or a URL and generate a QR code.
- Preview the generated QR code in the browser.
- Download the QR code as an image.
- Validate empty input and show useful errors.

## Tech stack

- **Frontend:** React
- **Backend:** FastAPI
- **QR generation:** Python QR-code library (for example, `qrcode` with Pillow)

## How it works

1. Enter text in the React interface.
2. The frontend sends it to the FastAPI endpoint.
3. The API creates a QR code image and returns it to the frontend.
4. Preview or download the resulting image.

## Getting started

### Prerequisites

- Python 3.10 or later
- Node.js 18 or later and npm

### Backend

From the backend directory, create and activate a virtual environment, install the project dependencies, and start the API:

```bash
python -m venv .venv
# macOS/Linux
source .venv/bin/activate
# Windows PowerShell
.venv\Scripts\Activate.ps1

pip install -r requirements.txt
uvicorn main:app --reload
```

The API will usually be available at `http://localhost:8000`. FastAPI's interactive API documentation is at `http://localhost:8000/docs`.

### Frontend

In a separate terminal, from the frontend directory:

```bash
npm install
npm run dev
```

Open the local URL printed by the development server (commonly `http://localhost:5173`). Configure the frontend's API base URL to point to the backend if the project does not already do so.

## API

The frontend should send the text to the QR-generation endpoint provided by the backend. A typical request might look like:

```http
POST /generate
Content-Type: application/json

{"text": "https://example.com"}
```

The response may be a PNG image or an encoded image URL, depending on the implementation. Check the FastAPI docs at `/docs` for the exact route and response format.

## Configuration

If the frontend and API run on different local ports, configure FastAPI CORS to allow the frontend's development origin. Keep the API URL in a frontend environment variable when possible; do not hard-code deployment-specific URLs in application code.

## Production

Build the React app with `npm run build`, then deploy the generated static files and FastAPI service using your preferred hosting setup. Set the production API URL and configure CORS for the deployed frontend origin.

## License

Add a license before redistributing this project.
