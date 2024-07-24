# EcomCore-API

## Project Description

EcomCore-API is a simplified e-commerce platform designed to demonstrate skills in implementing backend and frontend services using Laravel and Vue.js. This project is part of a technical test for a mid-level backend position and covers key aspects of architectural design, cloud implementation, RESTful service development, and API documentation.

## Architecture

<p align="center">
<img src="Architecture Implementation Diagram in AWS for E-commerce.drawio.png" width="800" alt="Architecture">
</p>

This project uses Laravel for the backend and Vue.js for the frontend. This architecture was chosen because:
- Laravel provides a robust PHP framework with excellent API support.
- Vue.js offers a reactive and user-friendly frontend framework.

### Diagram Description:

- **Frontend (Vue.js):** Interacts with the load balancer.
- **Load Balancer (ELB):** Distributes traffic among EC2 instances.
- **Laravel API:** Manages requests and is divided into two main services.
  - **Catalog Service:** Handles product management.
  - **Order Service:** Manages order processing.
- **MySQL:** Database for storing products and orders.
- **Redis:** Used for caching and queues.
- **Task Queue:** Processes asynchronous tasks.
- **Local Storage:** Used in development for static files.
- **S3:** Stores static files in production.
- **EC2:** Runs the Laravel application in the cloud.
- **RDS:** Provides a managed MySQL database.
- **ElastiCache:** Manages caching and queues.
- **CloudFront:** CDN serving static files.
- **IAM:** Manages permissions and access.
- **CloudWatch:** Monitors and logs application activity.

## Installation

Follow these steps to clone and install the project:

### Clone the Project

Clone the repository from GitHub:

```bash
git clone https://github.com/lokogam/EcomCore-API.git
cd EcomCore-API
```

## Requirements

Ensure you have the following requirements installed on your machine:

- Docker
- Docker Compose

## Environment Configuration

Copy the example configuration file and update the environment variables as needed:

```bash
cp .env.example .env
```

Add the following environment variables in the `.env` file:

```env
SANCTUM_STATEFUL_DOMAINS=localhost:8000
SESSION_DOMAIN=
SQS_PREFIX=http://localstack:4566/000000000000
SQS_QUEUE=your-queue-name
AWS_ACCESS_KEY_ID=test
AWS_SECRET_ACCESS_KEY=test
AWS_DEFAULT_REGION=us-east-1
AWS_BUCKET=your-bucket-name
AWS_ENDPOINT=http://localstack:4566
AWS_USE_PATH_STYLE_ENDPOINT=true
QUEUE_CONNECTION=sqs
```

## Installing Dependencies

Use Docker to install the project's dependencies with Composer:

```bash
docker run --rm \
    -u "$(id -u):$(id -g)" \
    -v "$(pwd):/var/www/html" \
    -w /var/www/html \
    laravelsail/php83-composer:latest \
    composer install --ignore-platform-reqs
```

## Bringing Up the Services

Use Docker Compose to bring up the services needed for the project:

```bash
./vendor/bin/sail up -d
```

## Generate Application Key

Generate the application key:

```bash
./vendor/bin/sail artisan key:generate
```

## Migrating the Database

Run the migrations to set up the database:

```bash
./vendor/bin/sail artisan migrate
```

## Execute AWS Setup

Run the AWS setup command:

```bash
./vendor/bin/sail artisan aws:setup 
```

## API Documentation

The API documentation is available at [http://localhost/api/documentation](http://localhost/api/documentation).

## Accessing the Application

The application will be available at [http://localhost](http://localhost).

### Frontend

You can find the frontend repository at: [VueShop-UI](https://github.com/lokogam/VueShop-UI.git)

---

Created by Duvan Gamboa  
Email: [duvangamboa8@gmail.com](mailto:duvangamboa8@gmail.com)  
LinkedIn: [Duvan Gamboa](https://www.linkedin.com/in/duvan-gamboa-5193951b2/)

