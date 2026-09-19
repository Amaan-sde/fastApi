# Simple FastAPI Server

A minimal FastAPI application with a single root route, `.env` port configuration, and Docker support.

## Project Structure



## Configuration

Set your desired port in `.env`:
```env
PORT=8000
```

## Running Locally

1. Create and activate a virtual environment:
   ```bash
   python3 -m venv venv
   source venv/bin/activate
   ```

2. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```

3. Run the development server (loads `PORT` from `.env` automatically):
   ```bash
   python main.py
   ```
   Or using uvicorn directly:
   ```bash
   uvicorn main:app --reload --host 0.0.0.0 --port $(grep PORT .env | cut -d '=' -f2)
   ```

4. Open [http://localhost:8000](http://localhost:8000) (or your configured port).
   - Interactive Swagger API docs: [http://localhost:8000/docs](http://localhost:8000/docs)

## Running with Docker

1. Build the Docker image:
   ```bash
   docker build -t fastapi-app .
   ```

2. Run the container with your `.env` file:
   ```bash
   docker run -d --env-file .env -p 8000:8000 --name fastapi-container fastapi-app
   ```
   *(Change the port mapping `-p <PORT>:<PORT>` to match the `PORT` in your `.env` if modified)*

3. Test the endpoint:
   ```bash
   curl http://localhost:8000/
   ```
