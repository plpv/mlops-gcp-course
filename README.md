# MLOps introductory course on Google Cloud Platform (GCP)

This course is taught as part of the [Master Year 2 Data Science Supaero](https://supaerodatascience.github.io/index.html).


<img src="https://www.isae-supaero.fr/wp-content/uploads/2025/03/logo.svg" width="150">

The course is designed around 5 classes of 3 hours each, for a total of 15 hours.

## A bit of context

MLOps is a rapidly evolving field that combines machine learning and software engineering to streamline the deployment, monitoring, and maintenance of machine learning models in production. As machine learning systems become increasingly complex, the need for robust workflows and efficient collaboration between data scientists and engineers grows. This class will focus on the tools and practices that enable teams to develop and deploy machine learning models at scale. The goal is to equip students with the skills necessary to manage the full lifecycle of machine learning models, from experimentation to deployment and monitoring, using industry-standard tools and platforms.

## Course syllabus

The course covers the fundamentals of MLOps, applied on Google Cloud Platform (GCP).

### Lecture slides

- What is MLOps?
- MLflow framework
- Vertex AI on GCP
- Deploying a model behind an endpoint on GCP — batch and streaming inference
- ML pipelines on GCP
- Deploying a RAG (Retrieval-Augmented Generation) chatbot on Vertex AI

### Classes

Lab notebooks can be found in the `labs` folder of this repository.

**Class 1**
- What is MLOps?
- Introduction to the MLflow framework
- MLflow lab on local computers

**Class 2**
- Introduction to GCP AI services (Vertex AI)
- Vertex AI hands-on lab

**Class 3**
- Deploying a model behind a Vertex AI endpoint
- Batch and streaming inference
- Scaling and A/B testing

**Class 4**
- ML pipelines on GCP

**Class 5**
- What is a RAG?
- Implementing a RAG on Vertex AI

## Installation

### Prerequisites

- Python
- Git
- GCP Account with credits

### Step 1: Clone the repository
```bash
git clone <repository-url>
cd MLOps-Introductory-Course-on-GCP
```

### Step 2: Installation (For Lab 1)

Navigate to the lab folder and create a virtual environment:
```bash
# macOS/Linux
cd labs/1_mlflow
python3.10 -m venv venv
source venv/bin/activate
pip install -r requirements.txt
```
```bash
# Windows — try these commands in order until one works
cd labs/1_mlflow

# Option 1: Python Launcher
py -3.10 -m venv venv

# Option 2: Direct Python command
python -m venv venv

# Option 3: Full path (adjust to your Python installation)
C:\Python310\python.exe -m venv venv

# Activate and install
venv\Scripts\activate
python --version  # Should show Python 3.10.x
pip install -r requirements.txt
```

### Evaluation

Hands-on implementation through notebooks, evaluated by the instructor.
  
## Acknowledgments

These are the lab materials for the MLOps course I teach as part of the AI specialization at ISAE-SUPAERO, developed in collaboration with HeadMind Partners AI. Thanks to ISAE-SUPAERO for their trust and support, especially Emmanuel Rachelson and Dennis Wilson.

Shared here for educational purposes.