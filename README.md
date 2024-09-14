# UserAccountHub API

## Overview

The UserAccountHub API is a robust web application designed to manage user accounts. Built using the Flask framework, this API allows for efficient CRUD operations, advanced querying, and reliable data management. It integrates seamlessly with PostgreSQL for data storage and employs Docker for containerization, ensuring a smooth and scalable deployment process. The application is equipped with a comprehensive suite of tests to validate functionality and ensure reliability.

## Table of Contents

* [Features](#features)
* [Tech Stack](#tech-stack)
* [Installation](#installation)
* [API Endpoints](#api-endpoints)
* [Tests](#tests)
* [Deployment](#deployment)
* [Kubernetes Deployment](#kubernetes-deployment)
* [License](#license)

## Features

- **CRUD Operations**: Create, Read, Update, and Delete user accounts.
- **Advanced Querying**: Filter accounts by name and other attributes.
- **Data Validation**: Ensures accurate and consistent data input.
- **Scalability**: Designed to handle a growing number of accounts and users.
- **Containerization**: Dockerized for consistent development and production environments.
- **Testing**: Includes unit and integration tests to ensure high quality and reliability.

## Tech Stack

- **Backend**: Flask, SQLAlchemy
- **Database**: PostgreSQL
- **Containerization**: Docker
- **Testing**: unittest, factory_boy
- **API Documentation**: Flask-RESTful
- **CI/CD**: Tekton

### Links

- [Flask](https://flask.palletsprojects.com/)
- [SQLAlchemy](https://www.sqlalchemy.org/)
- [PostgreSQL](https://www.postgresql.org/)
- [Docker](https://www.docker.com/)
- [Tekton](https://tekton.dev/)
- [unittest](https://docs.python.org/3/library/unittest.html)
- [factory_boy](https://factoryboy.readthedocs.io/)

## Installation

To get started with the UserAccountHub API, follow these steps:

1. Clone the Repository

   ```bash
   git clone https://github.com/InfectedDuck/UserAccountHub-API.git
   ```
2. Set up a virtual environment and install dependencies:

    ```bash
    python3 -m venv venv
    source venv/bin/activate
    pip install -r requirements.txt
    ```

3. Install Dependencies

    ```bash
    docker-compose up --build
    ```


5. Start the Flask Application

    ```bash
    python app.py
    ```

## API Endpoints

### GET /accounts

- **Description**: Retrieve a list of all accounts.
- **Response**: A list of accounts with their details.

### POST /accounts

- **Description**: Create a new account.
- **Request Body**: The details of the account to be created.
- **Response**: The details of the newly created account.

### GET /accounts/{id}

- **Description**: Retrieve an account by ID.
- **URL Parameters**: 
  - `id`: The ID of the account to retrieve.
- **Response**: Details of the account with the specified ID.

### PUT /accounts/{id}

- **Description**: Update an account by ID.
- **URL Parameters**: 
  - `id`: The ID of the account to update.
- **Request Body**: The updated details of the account.
- **Response**: The updated details of the account.

### DELETE /accounts/{id}

- **Description**: Delete an account by ID.
- **URL Parameters**: 
  - `id`: The ID of the account to delete.
- **Response**: Confirmation of deletion.

### GET /accounts/search?name={name}

- **Description**: Search for accounts by name.
- **Query Parameters**: 
  - `name`: The name of the account to search for.
- **Response**: A list of accounts matching the search criteria.
 

## Tests

### To ensure the application works as expected, run the tests:
    ```
    docker-compose exec web python -m unittest discover -s tests
    ```

## Deployment

Deploying the UserAccountHub API involves several steps:

### Containerization

The application is containerized using Docker. This process packages the application and its dependencies into a single container, simplifying deployment.

### Deployment Process

Follow the steps below to deploy the application:
1. **Build the Docker Image**: Create a Docker image of the application using the provided `Dockerfile`.
   ```bash
   docker build -t account-management-api .
   ```
3. **Run the Docker Container**: Start a container from the built Docker image to run the application.
   ```bash
   docker run -d -p 8080:8080 account-management-api
   ```
The application will be accessible at http://localhost:8080.

## Kubernetes Deployment

Deploying the Account Management API on Kubernetes involves creating and applying Kubernetes manifests for deployment and service management. Kubernetes provides a robust platform for managing containerized applications at scale.

### Create Deployment

Define a Kubernetes Deployment to manage the application's lifecycle, including scaling and rolling updates. 

### Create Service

Define a Kubernetes Service to expose the application and enable communication with other services.

### Apply Manifests

Apply the Kubernetes manifests to your cluster using the following command:

```bash
kubectl apply -f deployment.yaml
kubectl apply -f service.yaml
```
This will deploy the application and expose it based on the configuration specified in the manifests.

## License
This project is licensed under the Apache License 2.0. See the [LICENSE](LICENSE) file for details. <br>
This project is made as a part of IBM Course.
