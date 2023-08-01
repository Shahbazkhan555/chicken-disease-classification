# Chicken Disease Classification App

## Overview

This repository contains the code for a Chicken Disease Classification App, which uses Convolutional Neural Networks (CNN) to classify chicken fecal images and identify potential diseases. The project incorporates various MLOps concepts to ensure seamless development, reproducibility, and scalability. The app leverages DVC for pipeline tracking, employs CI/CD pipelines for automated testing and deployment, and utilizes Docker for containerization. Finally, the app is deployed on an AWS EC2 instance to make it accessible to users.

## Demo

![Chicken Disease Classification](chicken-demo.gif)

## Workflows

1. Update config.yaml
2. Update secrets.yaml [Optional]
3. Update params.yaml
4. Update the entity
5. Update the configuration manager in src config
6. Update the components
7. Update the pipeline 
8. Update the main.py
9. Update the dvc.yaml

## MLOps Concepts Used

### 1. Pipeline Development with DVC

DVC (Data Version Control) is used to track and manage the data pipeline. It allows us to version control data, intermediate results, and model artifacts. The pipeline includes data ingestion, base model preparation, model training, and model evaluation stages. Each stage is defined in the DVC pipeline, and DVC ensures that changes in data or code are tracked effectively.

### 2. CNN for Classification

The core of the project is based on Convolutional Neural Networks (CNNs), a powerful deep learning architecture widely used for image classification tasks. The CNN model is trained on labeled chicken fecal images to learn and identify various disease patterns accurately.

### 3. CI/CD Pipelines

Continuous Integration (CI) and Continuous Deployment (CD) pipelines are used to automate the testing and deployment processes. These pipelines ensure that changes pushed to the main branch are automatically tested and deployed to production after passing all tests. This automation reduces the chances of human error and increases the efficiency of the development process.

### 4. Docker Containerization

Docker is utilized for containerizing the application and its dependencies. Containerization ensures that the app runs consistently across different environments, making it easier to deploy and scale the application.

### 5. AWS EC2 Instance Deployment

1. **IAM User Setup:**
   - Create an IAM user with appropriate permissions for AWS services.
   - Assign policies like EC2FullAccess and ECRFullAccess to the IAM user.

2. **ECR Setup:**
   - Create an ECR repository to store Docker images securely.
   - Push your project's Docker image to the ECR repository.

3. **EC2 Instance Setup:**
   - Launch an EC2 instance and configure it with IAM role access to ECR.

4. **Deployment on EC2:**
   - SSH into the EC2 instance and pull the Docker image from ECR.
   - Run the Docker container on the EC2 instance.


## Important to note

1. **Command to run on EC2 to install Docker**
   - optinal

   - sudo apt-get update -y

   - sudo apt-get upgrade
	
   - required

   - curl -fsSL https://get.docker.com -o get-docker.sh

   - sudo sh get-docker.sh

   - sudo usermod -aG docker ubuntu

   - newgrp docker

2. **policy**
    - AmazonEC2ContainerRegistryFullAccess

    - AmazonEC2FullAccess

3. **Setup github secrets**

    - AWS_ACCESS_KEY_ID=

    - AWS_SECRET_ACCESS_KEY=

    - AWS_REGION = us-east-1

    - AWS_ECR_LOGIN_URI = demo>>  566373416292.dkr.ecr.ap-south-1.amazonaws.com

    - ECR_REPOSITORY_NAME = simple-app


## Project Structure

The repository is organized as follows:

- project/
	- .github/               # CI/CD workflows and related configurations
	- artifacts/             # DVC-tracked output artifacts
	- config/                # Configuration files
	- logs/                  # Log files (optional)
	- research/              # Folder for Jupyter Notebooks and research-related files
	- src/                   # Source code directory
		- cnnclassifier/      # Custom CNNClassifier package
		- components/    		# Helper components and utilities
		- config/        		# Configuration files for the CNNClassifier package
		- constants/     		# Constants used in the package
		- entity/        		# Entity classes (e.g., EvaluationConfig, PrepareBaseModelConfig)
		- pipeline/      		# DVC pipeline stages (stage_01_data_ingestion.py, stage_02_prepare_base_model.py, etc.)
		- utils/         		# Utility functions used in the package
		- templates/     		# Templates for various purposes
	- app.py             	   # Application entry point or main script
	- main.py                # Main script to orchestrate the project
	- dockerfile             # Docker configuration file
	- dvc.yaml               # DVC pipeline definition
	- params.yaml            # YAML file containing parameters for the pipeline stages
	- template.py            # Template file to create files and folders of project
	- scores.json            # Model evaluation scores
	- README.md              # Project documentation
	- requirements.txt       # Python dependencies
	- setup.py               # Setup script for installing the CNNClassifier package
	- .gitignore             # Git ignore file
	- .dockerignore          # Docker ignore file (if needed)


## Getting Started

### Prerequisites

1. Python 3.8 or higher installed on your system.
2. Docker installed to build and run the application as a container.

### Installation

1. Clone this repository to your local machine.

```bash
git clone https://github.com/your-username/chicken-disease-classification.git
cd chicken-disease-classification
```

2. Create and activate a virtual environment (optional but recommended).

```bash
python3 -m venv venv
source venv/bin/activate
```

3. Install the Python dependencies.

```bash
pip install -r requirements.txt
```

### Data Ingestion

To start the data ingestion stage, run:

```bash
dvc repro data_ingestion
```

### Prepare Base Model

To prepare the base model, run:

```bash
dvc repro prepare_base_model
```

### Training

To train the model, run:

```bash
dvc repro training
```

### Evaluation

To evaluate the model, run:

```bash
dvc repro evaluation
```

### Docker Containerization

To build the Docker image, run:

```bash
docker build -t chicken-classification-app .
```

### Deploying to AWS EC2

Deploy the Docker image on your AWS EC2 instance and expose the necessary ports to access the app.


## Contributing

Contributions are welcome! Please create a pull request with any improvements or bug fixes.

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

## Acknowledgments

Special thanks to all contributors and the open-source community for their valuable contributions.

## Contact

For any questions or feedback, please contact:

Shahbaz Khan
Email: mrkhan41998@email.com

