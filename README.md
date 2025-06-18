---
title: Iris Flower Prediction API
emoji: 🚀
colorFrom: indigo
colorTo: blue
sdk: docker
sdk_version: "1.0"
app_file: main.py
pinned: false
---

# Iris Flower Prediction API

This project is a demo MLOps application that serves a machine learning model for predicting the species of an iris flower based on its sepal length. The backend is built with FastAPI, and the model is trained using scikit-learn. A simple web UI is provided for user interaction.

## Features

- **Machine Learning Model**: Logistic Regression trained on the Iris dataset (using only sepal length as a feature).
- **REST API**: FastAPI backend with a `/predict` endpoint for predictions.
- **Web UI**: User-friendly HTML interface for making predictions.
- **Docker Support**: Easily containerize and run the application.

---

## Project Structure

```
mid-program-project-main/
│
├── main.py              # FastAPI app serving the model and UI
├── train.py             # Script to train and save the model
├── model/
│   └── model.joblib     # Pre-trained model file
├── ui/
│   └── index.html       # Web UI for predictions
├── requirements.txt     # Python dependencies
├── Dockerfile           # Docker configuration
└── tests/               # Test suite
```

---

## Setup & Execution

### 1. Clone the Repository

```sh
git clone <repo-url>
cd mid-program-project-main
```

### 2. (Recommended) Create and Activate a Virtual Environment

```sh
python3 -m venv venv
source venv/bin/activate
```

### 3. Install Dependencies

```sh
pip install --upgrade pip
pip install -r requirements.txt
pip install setuptools  # Required for Python 3.12+ to provide distutils
```

### 4. Train the Model (Optional)

If you want to retrain the model:

```sh
python train.py
```

This will generate `model/model.joblib`.

### 5. Run the Application

```sh
python main.py
```

The FastAPI server will start at [http://localhost:7860](http://localhost:7860).

---

## Using the Web UI

- Open your browser and go to [http://localhost:7860](http://localhost:7860).
- Enter a sepal length (in cm) and click "Predict".
- The predicted iris species will be displayed.

---

## API Usage

- **POST** `/predict`
  - **Request Body**: `{ "sepal_length": <float> }`
  - **Response**: `{ "prediction": "setosa" | "versicolor" | "virginica" }`

Example using `curl`:
```sh
curl -X POST "http://localhost:7860/predict" -H "Content-Type: application/json" -d '{"sepal_length": 5.1}'
```

---

## Running with Docker

1. **Build the Docker image:**
   ```sh
   docker build -t iris-predictor .
   ```

2. **Run the container:**
   ```sh
   docker run -p 7860:7860 iris-predictor
   ```

3. Access the app at [http://localhost:7860](http://localhost:7860).

---

## Running Tests

To run the test suite:
```sh
pytest
```

---

## Dependencies

- scikit-learn==1.5.0
- joblib==1.2.0
- fastapi
- uvicorn
- pydantic<2.0.0
- pytest-cov
- pytest-html
- httpx
- setuptools (for Python 3.12+)

---

## Notes

- If you use Python 3.12+, you must install `setuptools` to provide `distutils` for joblib compatibility.
- The UI and API are served from the same FastAPI server for simplicity.
- ------------
