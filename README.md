# Microservices Communication Using RabbitMQ

This project implements a microservices architecture using RabbitMQ for communication between services. Each service is responsible for a specific functionality and communicates through message queues.

## Services

### Stock Management Service
- **Functionality**: Handles stock management operations, including updating and deleting items in the inventory.
- **Database**: MySQL
- **RabbitMQ Queue**: `stock_management`
- **Port**: 5003

### Item Creation Service
- **Functionality**: Responsible for creating new items in the inventory.
- **Database**: MySQL
- **RabbitMQ Queue**: `item_creation`
- **Port**: 5002

### Health Check Service
- **Functionality**: Monitors the health of the application.
- **RabbitMQ Queue**: `health_check`
- **Port**: 5001

### Producer Service
- **Functionality**: Produces messages to various RabbitMQ queues based on HTTP requests.
- **Endpoints**:
  - `GET /health`: Sends a health check message.
  - `POST /item`: Creates a new item.
  - `PUT /inventory/<item_id>/stock`: Updates stock for an item.
  - `DELETE /inventory/<item_id>`: Deletes an item.
  - `POST /order`: Creates a new order.
- **Port**: 5000

## Setup
1. Clone the repository.
2. Set up the MySQL database and configure the environment variables.
3. Start RabbitMQ.
4. Run the services.

## Running the Services
You can run each service using the following bash commands:

For the Stock Management Service
```bash
python sm_cthree/stock_management.py &
```
For the Item Creation Service
```bash
python ic_ctwo/item_creation.py 
```
For the Health Check Service

```bash

python hc_cone/healthcheck.py 
```
For the Producer Service

```bash

python producer/producer.py &
```

5. Use a tool like Postman or curl to interact with the services via their respective endpoints.

## License
This project is licensed under the MIT License.
