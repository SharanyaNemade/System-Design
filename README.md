# System-Design


## 1. What is System Design?

System Design is the process of planning how a software system will handle:

* Users and traffic
* Data and storage
* Performance
* Failures
* Security
* Future growth

**Simple meaning:**
System Design is like creating the blueprint of an application before building it.

---

## 2. Why Do We Need System Design?

A small application may work with:

**User → Server → Database**

As users grow, one server may not be enough.

We may need:

* Multiple servers
* Load balancer
* Database scaling
* Cache
* Message queues
* CDN
* Replication
* Monitoring
* Security
* Backups

**Main purpose:** Decide when and why these components are required.

---

# 3. Main Goals of System Design

## Scalability

Ability to handle increasing users and requests.

### Vertical Scaling

Make one server more powerful:

* More CPU
* More RAM
* More storage

### Horizontal Scaling

Add more servers:

**Load Balancer → Server 1 / Server 2 / Server 3**

Horizontal scaling is important for large systems.

---

## Availability

System should remain accessible even when a server fails.

**Server 1 ❌ → Server 2 ✅**

Goal: Reduce downtime.

---

## Reliability

System should perform correctly and consistently.

Example: A bank transfer should not:

* Deduct money without crediting the receiver
* Deduct twice
* Lose the transaction
* Show incorrect balances

---

## Performance

Performance is how quickly the system responds.

Performance can be improved using:

* Caching
* Database indexing
* CDN
* Load balancing
* Efficient algorithms
* Database optimization

---

## Security

Protect:

* User accounts
* Passwords
* Personal data
* Payment data
* APIs
* Databases

Important areas:

* Authentication
* Authorization
* Encryption
* Attack prevention
* Permissions

---

## Maintainability

System should be easy to:

* Understand
* Modify
* Debug
* Extend

Large applications should be divided into logical components instead of one huge codebase.

---

# 4. Types of System Design

## HLD — High-Level Design

Focuses on the **big picture**.

Answers:

> What components do we need and how do they communicate?

Covers:

* Architecture
* Services
* Databases
* APIs
* Load balancers
* Caches
* Message queues
* Storage
* Communication
* Scalability
* Availability
* Security
* Deployment

---

## LLD — Low-Level Design

Focuses on **internal implementation**.

Deals with:

* Classes
* Objects
* Interfaces
* Methods
* Data structures
* Design patterns
* Class relationships
* Database tables
* Detailed API behavior

### Easy Difference

**HLD → What components do we need?**

**LLD → How do we build those components?**

---

# 5. Architectural Styles

## Monolithic Architecture

Most functionality exists in one application.

### Advantages

* Simple initially
* Easy to deploy
* Easy for small applications
* Less operational complexity

### Disadvantages

* Can become very large
* Individual scaling is difficult
* Problems can affect the whole application
* Can become difficult for large teams

---

## Microservices Architecture

Application is divided into independent services.

Examples:

* User Service
* Order Service
* Payment Service
* Notification Service

### Advantages

* Independent development
* Independent scaling
* Team independence
* Better failure isolation

### Disadvantages

* More complexity
* Network communication
* More complicated deployment
* Harder monitoring/debugging
* Distributed-system problems

**Monolith = One application**

**Microservices = Multiple smaller applications**

---

## Client-Server Architecture

**Client → Request → Server → Response → Client**

Example:

**Browser → HTTP Request → Web Server → Response**

Client handles user interaction; server handles processing and data access.

---

## Three-Tier Architecture

Three main layers:

1. **Presentation Layer** → User interface
2. **Business Layer** → Business rules
3. **Data Layer** → Data storage/retrieval

Common flow:

**Browser → Frontend → Backend → Database**

---

## Distributed System

Multiple computers work together as one system.

Example:

**Users → Load Balancer → Multiple Servers → Database Cluster**

Machines communicate through a network.

---

# 6. Important System Design Components

## Client

Sends requests to the system.

Examples:

* Browser
* Android app
* iOS app
* Desktop application
* Mobile app

---

## Server

Receives requests, processes them, and returns responses.

Example:

`GET /users/123`

---

## Load Balancer

Distributes requests across multiple servers.

**Users → Load Balancer → Server 1 / Server 2 / Server 3**

Improves traffic distribution and availability.

---

## Database

Stores application data such as:

* Users
* Orders
* Products
* Payments
* Messages

### Relational

Examples:

* SQL Server
* MySQL
* PostgreSQL
* Oracle

### NoSQL

Examples:

* MongoDB
* Cassandra
* DynamoDB

---

## Cache

Stores frequently accessed data for faster responses.

**Server → Cache → Fast Response**

If data is unavailable:

**Cache → Database → Cache → Response**

Examples:

* Redis
* Memcached

---

## Message Queue

Allows asynchronous processing.

Example:

**Order Service → Queue → Email Service**

The order service does not need to wait for email processing.

Examples:

* Kafka
* RabbitMQ
* Cloud queue services

---

## CDN

CDN delivers static content from servers closer to users.

Used for:

* Images
* Videos
* JavaScript
* CSS
* Files

Main benefit: Lower latency and better performance.

---

## API Gateway

Provides a single entry point for multiple services.

**Client → API Gateway → User / Order / Payment Services**

Can handle:

* Routing
* Authentication
* Rate limiting
* Request processing

---

# 7. Example: YouTube-Like System

Typical architecture:

**Users → CDN → Load Balancer → Application Servers**

Then:

* Database → User/video metadata
* Cache → Frequently accessed data
* Message Queue → Background processing
* Object Storage → Actual video files

---

# 8. Functional vs Non-Functional Requirements

## Functional Requirements

Describe **what the system does**.

Example:

* Register
* Login
* Search
* Order
* Payment
* Track delivery

## Non-Functional Requirements

Describe **how well the system works**.

Examples:

* Support millions of users
* Low response time
* High availability
* Security
* Failure handling
* Scalability

### Easy Memory Trick

**Functional = What**

**Non-Functional = How well**

---

# 9. System Designer's Process

A system designer generally follows:

1. **What are we building?**
2. **What should it do?**
3. **How many users/requests?**
4. **What data is required?**
5. **Where should data be stored?**
6. **How will high traffic be handled?**
7. **What happens if something fails?**
8. **How will the system be secured?**

---

# 10. Typical Modern System

**Users**

↓

**CDN**

↓

**Load Balancer**

↓

**Multiple Servers**

↓

**Cache + Database + Message Queue**

↓

**Storage + Background Workers**

---

# 11. System Design Learning Order

Learn in this sequence:

1. Client-Server Architecture
2. HTTP and APIs
3. Databases
4. SQL vs NoSQL
5. Indexing
6. Caching
7. Load Balancing
8. Vertical vs Horizontal Scaling
9. Replication
10. Sharding
11. Message Queues
12. CDN
13. Distributed Systems
14. Consistency and Availability
15. Fault Tolerance
16. Real System Design Problems

---

# 12. Practice System Design Problems

Practice designing:

* URL Shortener
* WhatsApp
* YouTube
* Instagram
* E-Commerce System
* Food Delivery System
* Ride-Sharing System
* Notification System

---

# 13. Most Important Concepts

### Scalability

* Load Balancer
* Caching
* Sharding

### Availability

* Replication
* Redundancy

### Reliability

* Failover
* Backups

### Performance

* Cache
* CDN
* Indexing

### Data Storage

* SQL
* NoSQL
* Replication
* Sharding

### Communication

* REST APIs
* Message Queues
* Events

---

# 14. Final Definition

**System Design = Planning the architecture, components, data flow, storage, communication, scalability, security, and reliability of a software system.**

### Remember

**HLD → Big Picture / Architecture**

**LLD → Detailed Implementation / Classes and Methods**





System-Design/
│
├── README.md
│
├── 01-Fundamentals/
│   ├── What-is-System-Design.md
│   ├── Functional-vs-Non-Functional-Requirements.md
│   ├── Scalability.md
│   ├── Availability.md
│   ├── Reliability.md
│   ├── Performance-and-Latency.md
│   ├── Bottlenecks.md
│   └── Trade-offs.md
│
├── 02-HLD/
│   │
│   ├── 01-Architecture-Basics/
│   │   ├── Client-Server.md
│   │   ├── Three-Tier-Architecture.md
│   │   ├── Monolithic-Architecture.md
│   │   ├── Microservices.md
│   │   └── Distributed-Systems.md
│   │
│   ├── 02-Scalability/
│   │   ├── Vertical-vs-Horizontal-Scaling.md
│   │   ├── Load-Balancing.md
│   │   ├── Stateless-vs-Stateful.md
│   │   └── Auto-Scaling.md
│   │
│   ├── 03-Databases/
│   │   ├── SQL-vs-NoSQL.md
│   │   ├── Database-Indexing.md
│   │   ├── Transactions.md
│   │   ├── ACID.md
│   │   ├── Database-Replication.md
│   │   ├── Read-Replicas.md
│   │   ├── Database-Sharding.md
│   │   └── Partitioning.md
│   │
│   ├── 04-Caching/
│   │   ├── What-is-Caching.md
│   │   ├── Cache-Strategies.md
│   │   ├── Cache-Aside.md
│   │   ├── Cache-Invalidation.md
│   │   ├── TTL.md
│   │   ├── Cache-Stampede.md
│   │   └── Redis.md
│   │
│   ├── 05-Communication/
│   │   ├── REST.md
│   │   ├── API-Gateway.md
│   │   ├── Synchronous-Communication.md
│   │   ├── Asynchronous-Communication.md
│   │   ├── Message-Queues.md
│   │   ├── RabbitMQ.md
│   │   ├── Kafka.md
│   │   └── Event-Driven-Architecture.md
│   │
│   ├── 06-Storage/
│   │   ├── File-Storage.md
│   │   ├── Object-Storage.md
│   │   ├── CDN.md
│   │   └── Pre-Signed-URLs.md
│   │
│   ├── 07-Security/
│   │   ├── Authentication.md
│   │   ├── Authorization.md
│   │   ├── JWT.md
│   │   ├── OAuth.md
│   │   ├── Rate-Limiting.md
│   │   ├── Encryption.md
│   │   └── Secrets-Management.md
│   │
│   ├── 08-Reliability/
│   │   ├── Fault-Tolerance.md
│   │   ├── Redundancy.md
│   │   ├── Failover.md
│   │   ├── Retry.md
│   │   ├── Exponential-Backoff.md
│   │   ├── Circuit-Breaker.md
│   │   ├── Idempotency.md
│   │   └── Graceful-Degradation.md
│   │
│   ├── 09-Distributed-Systems/
│   │   ├── CAP-Theorem.md
│   │   ├── Consistency.md
│   │   ├── Eventual-Consistency.md
│   │   ├── Distributed-Locks.md
│   │   └── Leader-Election.md
│   │
│   ├── 10-Observability/
│   │   ├── Logging.md
│   │   ├── Monitoring.md
│   │   ├── Metrics.md
│   │   ├── Distributed-Tracing.md
│   │   ├── Health-Checks.md
│   │   └── Alerting.md
│   │
│   ├── 11-Deployment/
│   │   ├── IIS.md
│   │   ├── Reverse-Proxy.md
│   │   ├── Containers.md
│   │   ├── Docker.md
│   │   ├── Load-Balancer-Deployment.md
│   │   └── CI-CD.md
│   │
│   └── 12-System-Design-Problems/
│       ├── URL-Shortener/
│       │   └── README.md
│       ├── Employee-Management-System/
│       │   └── README.md
│       ├── E-Commerce-System/
│       │   └── README.md
│       ├── Food-Delivery-System/
│       │   └── README.md
│       ├── Chat-Application/
│       │   └── README.md
│       ├── Notification-System/
│       │   └── README.md
│       ├── YouTube/
│       │   └── README.md
│       └── Ride-Sharing-System/
│           └── README.md
│
├── 03-LLD/
│   │
│   ├── 01-OOP/
│   │   ├── Classes-and-Objects.md
│   │   ├── Encapsulation.md
│   │   ├── Abstraction.md
│   │   ├── Inheritance.md
│   │   └── Polymorphism.md
│   │
│   ├── 02-SOLID/
│   │   ├── Single-Responsibility.md
│   │   ├── Open-Closed.md
│   │   ├── Liskov-Substitution.md
│   │   ├── Interface-Segregation.md
│   │   └── Dependency-Inversion.md
│   │
│   ├── 03-Design-Patterns/
│   │   ├── Creational/
│   │   │   ├── Singleton.md
│   │   │   ├── Factory.md
│   │   │   ├── Abstract-Factory.md
│   │   │   ├── Builder.md
│   │   │   └── Prototype.md
│   │   │
│   │   ├── Structural/
│   │   │   ├── Adapter.md
│   │   │   ├── Decorator.md
│   │   │   ├── Facade.md
│   │   │   └── Proxy.md
│   │   │
│   │   └── Behavioral/
│   │       ├── Strategy.md
│   │       ├── Observer.md
│   │       ├── Command.md
│   │       ├── State.md
│   │       └── Template-Method.md
│   │
│   ├── 04-UML/
│   │   ├── Class-Diagram.md
│   │   ├── Sequence-Diagram.md
│   │   ├── Activity-Diagram.md
│   │   └── State-Diagram.md
│   │
│   ├── 05-Data-Structures/
│   │   ├── Arrays.md
│   │   ├── Linked-List.md
│   │   ├── Stack.md
│   │   ├── Queue.md
│   │   ├── HashMap.md
│   │   ├── Trees.md
│   │   └── Graphs.md
│   │
│   └── 06-LLD-Problems/
│       ├── Parking-Lot/
│       │   └── README.md
│       ├── Library-Management-System/
│       │   └── README.md
│       ├── ATM/
│       │   └── README.md
│       ├── Elevator-System/
│       │   └── README.md
│       ├── Tic-Tac-Toe/
│       │   └── README.md
│       ├── Chess/
│       │   └── README.md
│       └── Car-Rental-System/
│           └── README.md
│
├── 04-Case-Studies/
│   ├── YouTube.md
│   ├── WhatsApp.md
│   ├── Instagram.md
│   ├── Amazon.md
│   ├── Uber.md
│   └── Netflix.md
│
├── 05-DotNet-System-Design/
│   ├── ASP.NET-Core-Architecture.md
│   ├── Web-API-Architecture.md
│   ├── Dependency-Injection.md
│   ├── Middleware.md
│   ├── Authentication-and-Authorization.md
│   ├── Distributed-Caching.md
│   ├── Background-Services.md
│   ├── API-Versioning.md
│   ├── Rate-Limiting.md
│   ├── Health-Checks.md
│   ├── Logging-and-Observability.md
│   └── Scaling-ASP.NET-Core.md
│
└── 06-Interview-Preparation/
    ├── HLD-Interview-Framework.md
    ├── LLD-Interview-Framework.md
    ├── Common-HLD-Questions.md
    ├── Common-LLD-Questions.md
    ├── System-Design-Cheatsheet.md
    └── Important-Trade-Offs.md
