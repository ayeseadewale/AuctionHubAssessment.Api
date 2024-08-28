
Introduction
The online auction platform facilitates real-time interactions among users during bidding. 
It allows users to enter a bidding room, submit bids, and notifies the highest bidder at the end of the auction. Additionally,
it automatically creates an invoice for the highest bidder.

System Architecture
The system is composed of several Controllers:

Room Service: Manages user entry into bidding rooms.
Bidding Service: Handles bid submissions and monitors the bidding process.
Notification Service: Sends real-time updates to users.
Invoice Service: Generates invoices for the highest bidders.
Payment Service: Processes payments based on generated invoices.
API Development
Language and Framework
Language: C#
Framework: ASP.NET Core
Key Operations
User Management:
Register
Login
Manage user profiles
Auction Management:
Create auction
Update auction
Delete auction
Bidding:
Submit bid
Retrieve current highest bid
Close auction
Messaging System Implementation
Preferred Tools
RabbitMQ
Celery
Apache Kafka
Communication Flow
Room Service to Bidding Service:
Trigger: User enters bidding room.
Action: Room Service sends a message to Bidding Service to start monitoring bids.
Bidding Service to Notification Service:
Trigger: Bid submission.
Action: Bidding Service sends real-time updates to Notification Service.
Notification Service to Invoice Service:
Trigger: Auction ends.
Action: Notification Service sends a message to Invoice Service to generate an invoice.
Invoice Service to Payment Service:
Trigger: Invoice generation.
Action: Invoice Service sends invoice details to Payment Service for processing.
Deployment
Dockerfiles
Create Dockerfiles for each Controllers.
Ensure each Dockerfile sets up the environment and dependencies correctly.
Kubernetes
Use Kubernetes for deploying and managing the Controllers.
Provide deployment scripts for setting up the services on cloud servers.
Setup Instructions
Clone the Repository:
git clone <repository-url>
cd <repository-directory>

Build and Run Docker Containers:
docker-compose up --build

Deploy to Kubernetes:
kubectl apply -f k8s/

Design Decisions
Repository Architecture: Chosen for scalability and maintainability.
Messaging System: RabbitMQ/Celery/Kafka selected for reliable and efficient communication between services.
ASP.NET Core: Selected for its robustness and support for building scalable APIs.

Note: This application was originally intended to be developed as a microservice architecture. 
However, due to time constraints and some unforeseen circumstances, I had to implement it using a repository design instead. 
If given more time, I would convert it to a microservice architecture.
