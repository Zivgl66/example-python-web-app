# Example Python Web App

This repository contains a basic Python web application built using Flask. The app serves as a simple template to demonstrate how to structure a Python web application and deploy it in various environments.

## Features

- Simple Python Flask web application.
- Can be deployed on local servers, cloud infrastructure, or containerized environments.
- Lightweight and easy to modify for demonstration or educational purposes.

## Prerequisites

To run this application, you need the following installed:

- Python 3.x
- Pip (Python package installer)
- (Optional) Docker for containerization

## Setup and Installation

### 1. Clone the repository

```bash
git clone https://github.com/Zivgl66/example-python-web-app.git
cd example-python-web-app
```

### 2. Install dependencies

Use `pip` to install the necessary Python packages.

```bash
pip install -r requirements.txt
```

### 3. Run the application

Start the Flask development server with:

```bash
python app.py
```

The app will be running at `http://127.0.0.1:3333/`.

## Docker Support

You can also run the application using Docker:

### 1. Build the Docker image

```bash
docker build -t python-web-app .
```

### 2. Run the Docker container

```bash
docker run -p 3333:3333 python-web-app
```

The app will now be accessible at `http://localhost:3333/`.

## Deployment

This app can be deployed on any platform that supports Python and Flask, including cloud platforms (AWS, GCP, Azure), Docker, or even Kubernetes clusters.
