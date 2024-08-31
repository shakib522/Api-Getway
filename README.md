# API Gateway

The API Gateway serves as the single entry point for all client requests in the quiz application microservices architecture. It routes incoming requests to the appropriate microservices, such as `quiz-service` and `question-service`, and provides a unified access layer to manage and secure APIs.

## Overview

The API Gateway plays a crucial role in managing communication between clients and backend services. It handles routing, load balancing, security, and can also be used for implementing rate limiting, authorization, and request/response transformations.

## Technologies Used

- **Spring Cloud Gateway**: A lightweight, scalable API Gateway that uses Spring Boot and integrates seamlessly with other Spring components.
- **OpenFeign**: For declarative REST clients to simplify service communication.
- **Eureka Client**: Registers the API Gateway with the Eureka Server for service discovery.
- **Eureka Server**: A service registry that allows the API Gateway to discover available microservices.

 ## Postman API Collection
 
[Quiz Craft.postman_collection.json](https://github.com/user-attachments/files/16823586/Quiz.Craft.postman_collection.json)

## Other Service repository
- Service Registry : https://github.com/shakib522/Service-Registry
- Question Service : https://github.com/shakib522/Question-Service
- Quiz Service : https://github.com/shakib522/Question-Service
## Prerequisites

- Java 17 or later
- Maven 3.6 or later
- Spring Boot 3.x
- Docker (optional, for containerization)

## Getting Started

### Clone the Repository

```bash
git clone <repository-url>
cd api-gateway
```


### Running the API Gateway

To start the API Gateway, run the following command from the root directory:

```bash
mvn spring-boot:run
```

Alternatively, you can package the application as a JAR and run it:

```bash
mvn clean package
java -jar target/api-gateway-0.0.1-SNAPSHOT.jar
```

### Accessing the API Gateway

The API Gateway will be accessible at:

```
http://localhost:<port>/
```

Requests routed through the API Gateway will be forwarded to the appropriate services based on the routes defined in the configuration. For example:

- `http://localhost:<port>/api/quizzes` will route to the `quiz-service`.
- `http://localhost:<port>/api/questions` will route to the `question-service`.

## Docker Support

### Build Docker Image

```bash
docker build -t api-gateway .
```

### Run Docker Container

```bash
docker run -d -p <port>:<port> --name api-gateway api-gateway
```

Ensure that the Eureka Server and the required microservices (`quiz-service` and `question-service`) are running and accessible to the Docker container.

## Features

- **Routing and Load Balancing**: Directs incoming traffic to the appropriate microservices and distributes the load among service instances.
- **Service Discovery**: Dynamically discovers available services via the Eureka Server.
- **Centralized Access Management**: Simplifies access control, monitoring, and logging by consolidating API management at a single entry point.

## Troubleshooting

- **Service Discovery Issues**: Ensure the API Gateway and microservices are correctly registered with the Eureka Server. Check Eureka Client configurations.
- **Routing Failures**: Verify the routes configured in `application.yml` match the service paths and names as registered in Eureka.
- **Performance Issues**: Monitor resource usage and consider scaling the API Gateway if it becomes a bottleneck.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Contact

For any questions or issues, please contact shakib at shakibhasann522@gmail.com
```

This README provides a comprehensive guide to set up and run the API Gateway in your microservices architecture. Customize it to fit your project's specifics and ensure all configurations match your actual environment!
