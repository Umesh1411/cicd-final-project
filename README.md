# CI/CD Final Project

[![Build Status](https://github.com/Umesh1411/cicd-final-project/actions/workflows/workflow.yml/badge.svg)](https://github.com/Umesh1411/cicd-final-project/actions)
[![License](https://img.shields.io/badge/License-Apache%202.0-blue.svg)](https://opensource.org/licenses/Apache-2.0)

## Overview

This project is the final capstone for the **Continuous Integration and Continuous Delivery (CI/CD)** course as part of the IBM DevOps and Software Engineering Professional Certificate.

It demonstrates an end-to-end cloud-native CI/CD pipeline using:
- **GitHub Actions** for automated linting (`flake8`) and unit testing (`nosetests`).
- **Tekton Pipelines** on **Red Hat OpenShift** for container building (`buildah`), automated testing, and zero-downtime deployment.
- **RESTful microservices** built in Python with Flask and PostgreSQL.

## Features

- **Automated Linting**: Uses `flake8` to enforce PEP 8 coding standards and catch syntactic errors.
- **Unit Testing with Code Coverage**: Uses `nosetests` with code coverage metrics targeting >95% test coverage.
- **Cloud-Native Deployment**: Deployed onto Red Hat OpenShift using declarative Tekton Tasks and Pipelines.
- **Containerization**: Rootless container image creation via `buildah`.

## Getting Started

### Prerequisites

- Python 3.9+
- Docker or Podman
- OpenShift CLI (`oc`)
- Tekton CLI (`tkn`)

### Running Locally

1. Clone this repository:
   ```bash
   git clone https://github.com/Umesh1411/cicd-final-project.git
   cd cicd-final-project
   ```

2. Install dependencies:
   ```bash
   pip install --upgrade pip
   pip install -r requirements.txt
   ```

3. Run linting:
   ```bash
   flake8 service --count --select=E9,F63,F7,F82 --show-source --statistics
   flake8 service --count --max-complexity=10 --max-line-length=127 --statistics
   ```

4. Run unit tests:
   ```bash
   nosetests -v --with-spec --spec-color --with-coverage --cover-package=service
   ```

5. Start the service:
   ```bash
   gunicorn --bind 0.0.0.0:8000 --log-level info service:app
   ```

## CI/CD Architecture

- **GitHub Actions**: Configured in `.github/workflows/workflow.yml`
- **Tekton Pipeline**: Configured in `.tekton/pipeline.yaml` and `.tekton/tasks.yaml`

## License

Copyright (c) 2026 Umesh Shinde. Licensed under the Apache License 2.0.
