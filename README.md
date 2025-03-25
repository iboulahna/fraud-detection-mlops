# fraud-detection-mlops

# Fraud Detection MLOps Pipeline — Palantir Foundry + AWS Integration

![palantir eng](https://github.com/user-attachments/assets/470b9a7c-da6f-49a2-a6cc-a352dba929c8)

This project implements a full **fraud detection pipeline** using a modern **MLOps architecture** combining **Palantir Foundry**, **Amazon SageMaker**, **MLflow**, and **Evidently AI**.

---

## Project Structure

fraud-detection-mlops/ 
├── config/ # Configuration files for MLflow and AWS 
├── transforms/ # Data transformation logic (Foundry Code Workbook) 
├── notebooks/ # Notebooks for training, monitoring, and drift detection 
├── api_service/ # REST API to serve the model 
├── workflows/ # Foundry Workflow orchestration pipeline 
├── models/ # Logical folder to store MLflow models 
├── requirements.txt # Python dependencies 
└── README.md # This file

fraud-detection-mlops/
├── README.md
├── .gitignore
├── config/
│   ├── mlflow_config.yaml
│   └── aws_integration.yaml
├── transforms/
│   └── prepare_data.py
├── notebooks/
│   ├── train_model.ipynb
│   ├── drift_detection.ipynb
│   └── model_monitoring.ipynb
├── api_service/
│   └── fraud_api.py
├── workflows/
│   └── fraud_pipeline.yaml
├── models/
│   └── README.md
└── requirements.txt
---

## MLOps Pipeline Overview

| Step                          | Tools Used                                       |
|------------------------------|--------------------------------------------------|
| Data ingestion               | Foundry Data Catalog + AWS S3/RDS                |
| Feature engineering          | Foundry Code Workbook (PySpark)                  |
| Model training               | LightGBM via Foundry ML + MLflow tracking        |
| Model deployment             | FastAPI + Foundry API Services                   |
| Model performance monitoring | MLflow Metrics                                   |
| Drift detection              | Evidently AI                                     |
| Auto re-training             | Foundry Workflow Orchestration                   |

---

## Run the API locally

Make sure to install the required dependencies:

```bash
pip install -r requirements.txt
```

Then run the API using Uvicorn:

```bash
uvicorn api_service.fraud_api:app --reload
```

The API will be available at:
http://127.0.0.1:8000/docs (Swagger interface)

```bash
curl -X POST http://127.0.0.1:8000/predict \
  -H "Content-Type: application/json" \
  -d '{"amount": 3400, "transaction_count": 17, "card_count": 4}'
```

Key Dependencies
- mlflow – Model tracking and management

- lightgbm – Fast and efficient ML model

- fastapi – Serve the model via REST API

- evidently – Drift detection and monitoring

- pandas, scikit-learn – Data handling and metrics
