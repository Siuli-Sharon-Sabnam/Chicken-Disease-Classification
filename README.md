# 🐔 Chicken Disease Classification Project

A Deep Learning-based classification system to detect diseases in chickens using image data, deployed with end-to-end CI/CD pipelines on AWS and Azure.

---

## 🚀 Tech Stack

<div align="center">

![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)
![TensorFlow](https://img.shields.io/badge/TensorFlow-FF6F00?style=for-the-badge&logo=tensorflow&logoColor=white)
![FastAPI](https://img.shields.io/badge/FastAPI-009688?style=for-the-badge&logo=fastapi&logoColor=white)
![Docker](https://img.shields.io/badge/Docker-2496ED?style=for-the-badge&logo=docker&logoColor=white)
![GitHub Actions](https://img.shields.io/badge/GitHub_Actions-2088FF?style=for-the-badge&logo=github-actions&logoColor=white)
![AWS](https://img.shields.io/badge/AWS-232F3E?style=for-the-badge&logo=amazon-aws&logoColor=white)
![Azure](https://img.shields.io/badge/Azure-0078D4?style=for-the-badge&logo=azure-devops&logoColor=white)
![DVC](https://img.shields.io/badge/DVC-945DD6?style=for-the-badge&logo=data-version-control&logoColor=white)

</div>

---

## 📁 Directory Structure

```
├── .github/workflows          # GitHub Actions CI/CD workflows
├── artifacts                  # DVC tracked data and model artifacts
├── configs                    # YAML config files
├── logs                       # Logging output
├── research                   # Experiments and notebooks
├── src                        # Core source code
├── templates                  # Frontend HTML templates
├── app.py                     # FastAPI entry point
├── dvc.yaml                   # DVC pipeline definition
├── Dockerfile                 # Docker configuration
├── requirements.txt           # Python dependencies
```


## 🔧 Project Workflow

1. Update `config.yaml`
2. Update `secrets.yaml` (Optional)
3. Update `params.yaml`
4. Define the ML entity
5. Configure managers in `src/config`
6. Implement components
7. Build pipeline logic
8. Run `main.py`
9. Manage pipeline via `dvc.yaml`

---

## 💻 How to Run Locally

### STEP 1: Clone the Repository
```bash
git clone https://github.com/Siuli-Sharon-Sabnam/Chicken-Disease-Classification.git
cd Chicken-Disease-Classification
```

### STEP 2: Create and Activate a Conda Environment
```bash
conda create -n cnncls python=3.8 -y
conda activate cnncls
```

### STEP 3: Install Requirements
```bash
pip install -r requirements.txt
```

### STEP 4: Run the App
```bash
python app.py
```
> Access via `localhost:<PORT>`

---

## 🌀 DVC Commands

```bash
dvc init
dvc repro
dvc dag
```

---

## 🚢 AWS CI/CD Deployment with GitHub Actions

1. **Login to AWS Console**
2. **Create IAM User** with:
   - `AmazonEC2ContainerRegistryFullAccess`
   - `AmazonEC2FullAccess`
3. **Create an ECR Repo**
   - Save URI e.g., `566373416292.dkr.ecr.us-east-1.amazonaws.com/chicken`
4. **Launch EC2 Instance (Ubuntu)**
5. **Install Docker** in EC2:
   ```bash
   sudo apt-get update -y
   sudo apt-get upgrade -y
   curl -fsSL https://get.docker.com -o get-docker.sh
   sudo sh get-docker.sh
   sudo usermod -aG docker ubuntu
   newgrp docker
   ```

6. **Set up EC2 as GitHub Self-hosted Runner**:  
   Go to `Settings > Actions > Runners`

7. **Set GitHub Secrets**
   - `AWS_ACCESS_KEY_ID`
   - `AWS_SECRET_ACCESS_KEY`
   - `AWS_REGION` = `us-east-1`
   - `AWS_ECR_LOGIN_URI`
   - `ECR_REPOSITORY_NAME`

---

## ☁ Azure CI/CD Deployment with GitHub Actions

### Docker Commands
```bash
docker build -t chickenapp.azurecr.io/chicken:latest .
docker login chickenapp.azurecr.io
docker push chickenapp.azurecr.io/chicken:latest
```

### Azure Deployment Steps
1. Build Docker Image
2. Push to Azure Container Registry
3. Launch Azure Web App
4. Pull and Run Docker Image

---
