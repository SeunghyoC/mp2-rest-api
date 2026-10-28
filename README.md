# MP2: Data Processing REST API

This FastAPI app lets users upload a CSV, clean it with the MP1 pipeline, and retrieve the cleaned data through HTTP requests. `POST /upload` stores a CSV in memory and returns a dataset ID. `POST /datasets/{dataset_id}/process` validates the data and removes duplicates, missing values, and outliers based on the settings in the request body, then returns a cleaning report. `GET /datasets/{dataset_id}` returns the stored rows, and `GET /health` checks that the server is running. Every request is logged with a request ID, status code, and duration, and the API is tested with pytest and TestClient.

## Project Structure

- `main.py`: creates the app and defines the endpoints
- `src/`: models, in-memory storage, logging setup, and middleware
- `data_pipeline/`: reused MP1 modules for validation and cleaning
- `fixtures/sample_data.csv`: sample data
- `tests/`: API tests

## Run

```bash
python -m pip install -r requirements.txt
python -m uvicorn main:app --reload
```

Open http://127.0.0.1:8000/docs.

## Test

```bash
python -m pytest tests -v
```
