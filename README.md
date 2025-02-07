Dưới đây là một tệp `README.md` bằng tiếng Anh để thiết lập dự án của bạn:

---

# E-commerce Microservices Platform

This project is an e-commerce platform built with a microservices architecture. It includes the following services:

1. **API Gateway**: Handles routing and API composition.
2. **Auth Service**: Manages authentication and authorization.
3. **User Service**: Manages user accounts (NestJS + PostgreSQL).
4. **Product Service**: Manages products and categories (NestJS + MongoDB).
5. **Cart Service**: Manages shopping carts (NestJS + Redis).
6. **Order Service**: Manages orders and shipping status (NestJS + PostgreSQL).
7. **Payment Service**: Handles payments (NestJS + Stripe + Kafka).
8. **Notification Service**: Sends notifications (email, SMS) (NestJS + Kafka/SQS).

---

## Prerequisites

Before you begin, ensure you have the following installed:

- **Node.js** (v16 or higher)
- **NestJS CLI** (`npm install -g @nestjs/cli`)
- **Docker** and **Docker Compose**
- **Git**

---

## Project Structure

```
📦 ECommerceMicroservices
┣ 📁 apps                         # Contains all microservices
┃ ┣ 📁 api-gateway                # API Gateway (GraphQL or REST, using NestJS)
┃ ┣ 📁 auth-service               # Authentication service (JWT, OAuth)
┃ ┣ 📁 user-service               # User management service (PostgreSQL)
┃ ┣ 📁 product-service            # Product management service (MongoDB)
┃ ┣ 📁 cart-service               # Cart management service (Redis)
┃ ┣ 📁 order-service              # Order management service (PostgreSQL)
┃ ┣ 📁 payment-service            # Payment processing service (Stripe, Kafka)
┃ ┗ 📁 notification-service       # Notification service (Kafka, SQS, Email)
┣ 📁 libs                         # Shared libraries
┃ ┣ 📁 common                     # BaseEntity, Exceptions, Logger, etc.
┃ ┣ 📁 contracts                  # DTOs, Interfaces, Event Patterns
┃ ┣ 📁 event-bus                  # Wrapper for Kafka/RabbitMQ/SQS
┃ ┗ 📁 utils                      # Helpers (date formatting, hashing, validation)
┣ 📁 deployments                  # Deployment files for Docker/Kubernetes/Terraform
┃ ┣ 📁 k8s                        # Kubernetes manifests
┃ ┣ 📁 docker                     # Docker Compose files
┃ ┗ 📁 terraform                  # Infrastructure as Code (AWS/GCP)
┣ 📁 tests                        # End-to-End, Integration, and Load Testing
┣ 📁 docs                         # Project documentation
┣ 📜 .env                         # Environment variables
┣ 📜 .gitignore                   # Git ignore file
┣ 📜 docker-compose.yml           # Docker Compose file for local development
┣ 📜 nest-cli.json                # NestJS CLI configuration
┣ 📜 package.json                 # Project dependencies
┣ 📜 README.md                    # Project README
┣ 📜 tsconfig.json                # TypeScript configuration
┗ 📜 eslint.json                  # ESLint configuration
```

---

## Setup Instructions

### 1. Clone the Repository

```bash
git clone https://github.com/your-username/e-commerce-microservices.git
cd e-commerce-microservices
```

### 2. Install Dependencies

Install dependencies for each service:

```bash
cd apps/api-gateway && npm install && cd ../..
cd apps/auth-service && npm install && cd ../..
cd apps/user-service && npm install && cd ../..
cd apps/product-service && npm install && cd ../..
cd apps/cart-service && npm install && cd ../..
cd apps/order-service && npm install && cd ../..
cd apps/payment-service && npm install && cd ../..
cd apps/notification-service && npm install && cd ../..
```

### 3. Set Up Environment Variables

1. Create a `.env` file in the root directory:
   ```bash
   touch .env
   ```
2. Add the required environment variables for each service. For example:
   ```env
   # PostgreSQL
   POSTGRES_USER=user
   POSTGRES_PASSWORD=password
   POSTGRES_DB=user_db

   # MongoDB
   MONGO_URI=mongodb://localhost:27017/product_db

   # Redis
   REDIS_HOST=localhost
   REDIS_PORT=6379

   # Stripe
   STRIPE_SECRET_KEY=your-stripe-secret-key

   # Kafka
   KAFKA_BROKER=localhost:9092
   ```

### 4. Start Docker Containers

Run the following command to start PostgreSQL, MongoDB, Redis, and Kafka using Docker Compose:

```bash
docker-compose up -d
```

### 5. Run the Services

Start each microservice individually:

```bash
# API Gateway
cd apps/api-gateway && npm run start:dev && cd ../..

# Auth Service
cd apps/auth-service && npm run start:dev && cd ../..

# User Service
cd apps/user-service && npm run start:dev && cd ../..

# Product Service
cd apps/product-service && npm run start:dev && cd ../..

# Cart Service
cd apps/cart-service && npm run start:dev && cd ../..

# Order Service
cd apps/order-service && npm run start:dev && cd ../..

# Payment Service
cd apps/payment-service && npm run start:dev && cd ../..

# Notification Service
cd apps/notification-service && npm run start:dev && cd ../..
```

---

## API Endpoints

### User Service
- `POST /users`: Create a new user
- `GET /users`: Get a list of users

### Product Service
- `POST /products`: Create a new product
- `GET /products`: Get a list of products

### Cart Service
- `POST /cart/:userId`: Add a product to the cart
- `GET /cart/:userId`: Get the user's cart

### Order Service
- `POST /orders`: Create a new order
- `GET /orders`: Get a list of orders

### Payment Service
- `POST /payments`: Process a payment

### Notification Service
- `POST /notifications`: Send a notification

---

## Testing

To run tests for each service, navigate to the service directory and run:

```bash
npm run test
```

---

## Deployment

### Docker

1. Build Docker images for each service:
   ```bash
   docker build -t api-gateway ./apps/api-gateway
   docker build -t auth-service ./apps/auth-service
   docker build -t user-service ./apps/user-service
   docker build -t product-service ./apps/product-service
   docker build -t cart-service ./apps/cart-service
   docker build -t order-service ./apps/order-service
   docker build -t payment-service ./apps/payment-service
   docker build -t notification-service ./apps/notification-service
   ```
2. Deploy using Docker Compose:
   ```bash
   docker-compose up -d
   ```

### Kubernetes

1. Apply Kubernetes manifests:
   ```bash
   kubectl apply -f deployments/k8s/
   ```

---

## Contributing

Contributions are welcome! Please follow these steps:
1. Fork the repository.
2. Create a new branch (`git checkout -b feature/your-feature`).
3. Commit your changes (`git commit -m 'Add some feature'`).
4. Push to the branch (`git push origin feature/your-feature`).
5. Open a Pull Request.

---

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

---

## Contact

If you have any questions, feel free to reach out:
- Email: your-email@example.com
- GitHub: [your-username](https://github.com/your-username)

---

Happy coding! 🚀