# Medical-chatbot-using-RAG
I am creating a Medical chat bot webapp using RAG, LLM, Python, Langchain, Flask, also deployed in AWS using Docker
# STEP 01 — Clone the Repository

git clone https://github.com/entbappy/Build-a-Complete-Medical-Chatbot-with-LLMs-LangChain-Pinecone-Flask-AWS.git
cd Build-a-Complete-Medical-Chatbot-with-LLMs-LangChain-Pinecone-Flask-AWS

# STEP 02 — Create the Environment (MAC)
uv python install 3.10
uv venv --python 3.10
source .venv/bin/activate

# STEP 03 — Install Dependencies
pip install --upgrade pip
pip install -r requirements.txt

# STEP 04 — Create .env File
touch .env
open .env

# STEP 05 — Store Embeddings into Pinecone
python store_index.py

STEP 06 — Run the App
python app.py


Open browser:

http://localhost:5000

✅ AWS + GitHub Actions CI/CD (MAC VERSION)

AWS steps are the same, but I am rewriting them cleanly for Mac developers.

STEP 1 — AWS Login

Sign in normally.

STEP 2 — Create IAM User (Deployment User)

Create a new IAM user with:

Permissions to attach:
AmazonEC2ContainerRegistryFullAccess
AmazonEC2FullAccess


Save:

Access Key ID

Secret Access Key

STEP 3 — Create ECR Repository

Example name:

medicalbot


Save the URI:

315865595366.dkr.ecr.us-east-1.amazonaws.com/medicalbot

STEP 4 — Create EC2 Instance (Ubuntu)

Recommended:

t2.medium or t3.medium

Ubuntu 22.04

Open and install docker:

sudo apt-get update -y
sudo apt-get upgrade -y
curl -fsSL https://get.docker.com -o get-docker.sh
sudo sh get-docker.sh
sudo usermod -aG docker ubuntu
newgrp docker

STEP 5 — Configure EC2 as GitHub Runner

Go to:

GitHub Repo → Settings → Actions → Runners → New self-hosted runner


Choose → Linux

Run all commands provided by GitHub.

STEP 6 — Set GitHub Secrets

Go to:

Repo → Settings → Secrets → Actions


Add these secrets:

AWS_ACCESS_KEY_ID
AWS_SECRET_ACCESS_KEY
AWS_DEFAULT_REGION (example: us-east-1)
ECR_REPO
PINECONE_API_KEY
OPENAI_API_KEY


Since you're on Mac, you don’t need any special conversion — values are the same.

Example:

Secret Name	Value
AWS_ACCESS_KEY_ID	AKIAxxxxxx
AWS_SECRET_ACCESS_KEY	xxxxxxxxxxxxxxxxx
AWS_DEFAULT_REGION	us-east-1
ECR_REPO	315865595366.dkr.ecr.us-east-1.amazonaws.com/medicalbot
PINECONE_API_KEY	xxxx
OPENAI_API_KEY	xxxx