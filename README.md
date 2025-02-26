# LLM-Deployment-with-MLflow
This project walks through deploying an open-source Large Language Model (LLM) using MLflow Model Registry and MLflow Deployments. It also covers model governance and access control to ensure secure usage.

## Whats Inside?
✅ Train an LLM (facebook/opt-350m) on the AG News dataset
✅ Log model, tokenizer, and metrics using MLflow Tracking
✅ Register the trained model in MLflow Model Registry
✅ Deploy the model via MLflow Deployments (REST API)
✅ Implement access control using an API key
✅ Optional: Deploy to AWS SageMaker, Azure ML, or GCP Vertex AI

## Setup Instructions
1️⃣ Install Dependencies
    pip install mlflow transformers torch datasets flask
2️⃣ Train and Log the Model
    Run the training script to log and register the model:
    python train_model.py
3️⃣ Serve the Model via REST API
    mlflow models serve -m "models:/LLM-Text-Classifier/Production" -p 5001
4️⃣ Secure the API with an API Key
    Start the secure Flask API:
    python secure_api.py
  Make a prediction request with authentication:
  curl -X POST "http://127.0.0.1:5002/predict" \
     -H "x-api-key: secure-api-key" \
     -H "Content-Type: application/json" \
     -d '{"text": "Breaking news: AI is transforming industries!"}'

## Deployment Options
For cloud deployment, use MLflow Deployments:
mlflow deployments create -t sagemaker --name llm-text-classifier --model-uri "models:/LLM-Text-Cl
