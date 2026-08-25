# System-Design



What is System Design?

System Design is the process of planning how a software system should be built so that it can handle users, data, traffic, failures, security, and future growth.

In simple words:

System design is like creating the blueprint of a software application before building it.

For example, imagine you want to build YouTube.

You need to think about:

Where will videos be stored?
How will users upload videos?
How will millions of people watch videos at the same time?
How will videos load quickly?
Where will user information be stored?
What happens if one server crashes?
How will recommendations work?
How will the system handle 100 users today and 100 million users tomorrow?

All of these questions are part of system design.

A Simple Real-World Example

Think about building a house.

Before constructing it, you create a plan:

                 HOUSE
                   |
        +----------+----------+
        |          |          |
     Bedroom    Kitchen    Bathroom
        |
     Electricity
        |
     Plumbing


You decide:

Where each room goes
Where electricity goes
Where water pipes go
How much material is needed
How many people the house should accommodate

Software systems are similar.

Before writing thousands or millions of lines of code, we decide:

                  APPLICATION
                       |
          +------------+------------+
          |            |            |
       Frontend      Backend      Database
                         |
              +----------+----------+
              |          |          |
           Cache      Message      Storage
                      Queue


That overall planning is System Design.

Why Do We Need System Design?

A small application might work perfectly with just one server.

For example:

User → Server → Database


Suppose you have only 100 users. This may be enough.

But imagine your application becomes popular:

1 user
   ↓
100 users
   ↓
10,000 users
   ↓
1 million users
   ↓
100 million users


Now one server may not be enough.

You may need:

Multiple servers
Load balancers
Databases
Caches
Message queues
CDNs
Replication
Monitoring
Security mechanisms
Backup systems

System design helps us decide when and why we need these components.

Main Goals of System Design

A good system should generally have several important qualities.

1. Scalability

Scalability means the system can handle an increasing number of users or requests.

For example:

Today:

1,000 users
     ↓
1 server


Tomorrow:

1,000,000 users
     ↓
10 servers


The system should be designed so that we can increase capacity without completely rebuilding everything.

There are two common approaches:

Vertical Scaling

Make one machine more powerful.

Small Server
    ↓
More CPU
More RAM
More Storage
    ↓
Powerful Server

Horizontal Scaling

Add more machines.

       Load Balancer
       /     |      \
 Server 1  Server 2  Server 3


Horizontal scaling is very important in large distributed systems.

2. Availability

Availability means the system should remain accessible when users need it.

Imagine an online shopping website.

If one server crashes:

Server 1 ❌


Users should still be able to use the application through another server:

        Load Balancer
        /           \
   Server 1 ❌    Server 2 ✅
                    |
                  Users


The goal is to reduce downtime.

3. Reliability

Reliability means the system should perform correctly and consistently.

For example, if a bank transfers:

₹10,000


from Account A to Account B, the system must not accidentally:

Deduct ₹10,000 but not add it to B
Deduct it twice
Lose the transaction
Show incorrect balances

A reliable system handles these situations carefully.

4. Performance

Performance means how quickly the system responds.

For example:

User → Request → Server → Response


If the response takes:

50 ms    → Excellent
500 ms   → Usually acceptable
5 sec    → User may become frustrated


System design considers ways to improve performance using things like:

Caching
Database indexing
CDNs
Load balancing
Efficient algorithms
Database optimization
5. Security

System design must also protect:

User accounts
Passwords
Personal information
Payment information
APIs
Databases

For example:

User
 ↓
Authentication
 ↓
Authorization
 ↓
Application
 ↓
Database


You need to determine:

Who can access what?
How are passwords stored?
How is data encrypted?
How are attacks prevented?
How are permissions managed?
6. Maintainability

A system should be easy for developers to understand, modify, debug, and extend.

For example, if your application has:

Authentication
Payment
Orders
Notifications
Search
Recommendations


You don't want everything mixed together in one huge piece of code.

Instead, you can organize the system into logical components.

Types of System Design

There are several ways to classify system design.

The two most important categories you'll hear about are:

High-Level Design (HLD)
Low-Level Design (LLD)

Let's understand both.

1. High-Level Design (HLD)

HLD = High-Level Design

HLD focuses on the big picture.

It answers:

"What major components does our system need, and how do they communicate?"

For example, imagine designing an e-commerce application.

A high-level design could look like:

                 Users
                   |
                   ↓
              Load Balancer
                   |
          +--------+--------+
          |        |        |
       Server   Server   Server
          |        |        |
          +--------+--------+
                   |
        +----------+----------+
        |          |          |
     Database    Cache    Message Queue


At this level, we are not discussing individual classes or functions.

We are discussing architecture.

HLD typically covers:
System architecture
Services
Databases
APIs
Load balancers
Caches
Message queues
Storage
Communication between services
Scalability
Availability
Security
Deployment
2. Low-Level Design (LLD)

LLD = Low-Level Design

LLD focuses on the internal implementation of components.

Suppose HLD says:

User Service


LLD asks:

"How exactly should User Service be implemented?"

You might design:

User
 ├── userId
 ├── name
 ├── email
 └── password

UserService
 ├── createUser()
 ├── getUser()
 ├── updateUser()
 └── deleteUser()


LLD deals with things such as:

Classes
Objects
Interfaces
Methods
Data structures
Design patterns
Relationships between classes
Database tables
Detailed API behavior
HLD vs LLD
HLD	LLD
Big picture	Detailed picture
Architecture	Implementation
Major components	Classes and methods
Services	Objects
Databases	Tables/schema details
APIs between systems	API implementation details
Scalability	Code-level design
Used for architecture decisions	Used for development

A simple way to remember:

HLD = What components do we need?
LLD = How do we build those components?

Other Important Types / Architectural Styles

System design can also be discussed in terms of architecture styles.

3. Monolithic Architecture

In a monolithic architecture, most or all functionality is part of one application.

For example:

             Application
                  |
     +------------+------------+
     |            |            |
   Users        Orders       Payments
     |            |            |
     +------------+------------+
                  |
              Database


Everything is deployed together.

Advantages
Simple to develop initially
Easy to deploy
Easy to understand for small applications
Usually simpler operationally
Disadvantages
Can become very large
Scaling individual features can be difficult
A problem in one area can affect the whole application
Large teams can find development harder as the system grows

A small startup might start with a monolith and later evolve its architecture.

4. Microservices Architecture

In microservices, the application is divided into smaller independent services.

For example:

                 API Gateway
                      |
       +--------------+--------------+
       |              |              |
   User Service   Order Service   Payment Service
       |              |              |
   User DB        Order DB       Payment DB


Each service focuses on a particular business responsibility.

For example:

User Service → users
Order Service → orders
Payment Service → payments
Notification Service → notifications
Advantages
Services can be developed independently
Services can be scaled independently
Teams can work independently
Failure can sometimes be isolated to one service
Disadvantages
More complicated
Network communication is involved
Deployment is more complicated
Monitoring and debugging become harder
Distributed-system problems appear

So:

Monolith = one large application
Microservices = multiple smaller applications working together

5. Client-Server Architecture

This is one of the most fundamental architectures.

Client
   |
   | Request
   ↓
Server
   |
   | Response
   ↓
Client


For example, when you open a website:

Browser
   |
   | HTTP Request
   ↓
Web Server
   |
   | Response
   ↓
Browser


The client is usually responsible for interacting with the user.

The server handles processing, business logic, data access, etc.

6. Three-Tier Architecture

A very common architecture is three-tier architecture.

        Presentation Layer
              ↓
        Business Layer
              ↓
         Data Layer

Presentation Layer

What the user interacts with.

Examples:

Website
Mobile application
Web UI
Business Layer

Contains business rules.

For example:

Is the user allowed to purchase this product?

Data Layer

Responsible for storing and retrieving data.

For example:

MySQL
PostgreSQL
MongoDB


A more concrete example:

Browser
   ↓
Frontend
   ↓
Backend
   ↓
Database


This is extremely common.

7. Distributed System

A distributed system consists of multiple computers working together as one overall system.

Instead of:

        One Server
           |
        Database


you might have:

              Users
                |
          Load Balancer
                |
      +---------+---------+
      |         |         |
   Server 1  Server 2  Server 3
      |         |         |
      +---------+---------+
                |
          Database Cluster


These machines communicate over a network.

Large systems such as search engines, social networks, streaming platforms, and cloud services commonly use distributed architectures.

Important Components in System Design

When learning system design, you'll repeatedly encounter certain components.

1. Client

The client sends requests to your system.

Examples:

Browser
Android app
iOS app
Desktop application
Mobile App
    ↓
Request

2. Server

The server receives requests and performs operations.

Client
  ↓
Server
  ↓
Response


For example:

GET /users/123


The server processes the request and returns user information.

3. Load Balancer

Suppose you have three servers:

Server 1
Server 2
Server 3


Instead of users directly choosing a server, a load balancer distributes requests.

             Users
               |
               ↓
         Load Balancer
          /     |     \
         ↓      ↓      ↓
      Server 1 Server 2 Server 3


It helps distribute traffic and can improve availability.

4. Database

A database stores information.

For example:

Users
Orders
Products
Payments
Messages


Common database categories include:

Relational databases

Examples:

PostgreSQL
MySQL
SQL Server
Oracle Database

They typically store structured data in tables.

Users

id | name | email
---|------|------
1  | Rahul| ...
2  | Priya| ...

NoSQL databases

Examples include:

MongoDB
Cassandra
DynamoDB

They are often useful for particular large-scale or flexible-data workloads.

5. Cache

A cache stores frequently accessed data temporarily so it can be returned faster.

Without cache:

User
 ↓
Server
 ↓
Database
 ↓
Response


With cache:

User
 ↓
Server
 ↓
Cache
 ↓
Fast Response


If the data isn't in the cache:

Server
  ↓
Cache ❌
  ↓
Database
  ↓
Cache ← Store result
  ↓
Response


Popular caching technologies include Redis and Memcached.

6. Message Queue

Sometimes one component shouldn't have to wait for another component to finish.

For example, after placing an order:

User
 ↓
Order Service
 ↓
Order Created


Sending an email might take additional time.

Instead:

Order Service
      |
      ↓
Message Queue
      |
      ↓
Email Service


The order service can continue while the email service processes the message asynchronously.

Common technologies include Kafka, RabbitMQ, and cloud queue services.

7. CDN

CDN = Content Delivery Network

A CDN helps deliver static content such as:

Images
Videos
JavaScript
CSS
Files

from servers geographically closer to users.

For example:

User in India
      ↓
India CDN Server
      ↓
Image


rather than always retrieving the image from a server located far away.

This can reduce latency and improve performance.

8. API Gateway

In a microservices architecture, you may have many services:

User Service
Order Service
Payment Service
Product Service


Instead of the client communicating directly with every service:

Mobile App
   |
   +---- User Service
   +---- Order Service
   +---- Payment Service


you can use an API Gateway:

             Mobile App
                  |
                  ↓
             API Gateway
          /      |       \
         ↓       ↓        ↓
      User    Order    Payment
     Service  Service   Service


The gateway can handle things such as:

Routing
Authentication
Rate limiting
Request processing
A Complete Simple System

Let's imagine we're designing a YouTube-like video platform.

At a high level:

                       Users
                         |
                         ↓
                    CDN / Edge
                         |
                         ↓
                   Load Balancer
                         |
             +-----------+-----------+
             |           |           |
          Server 1    Server 2    Server 3
             |           |           |
             +-----------+-----------+
                         |
             +-----------+-----------+
             |           |           |
          Database      Cache     Message Queue
             |                       |
             ↓                       ↓
         User Data              Processing
                                      |
                                      ↓
                                  Video Storage


Now consider what each component does.

User

Watches or uploads videos.

CDN

Delivers videos quickly to users.

Load Balancer

Distributes requests among servers.

Application Servers

Handle:

Login
Video metadata
Comments
Likes
Subscriptions
Search
Database

Stores:

Users
Video metadata
Comments
Likes
Subscriptions
Cache

Stores frequently accessed information.

Message Queue

Handles background work such as video processing.

Object Storage

Stores the actual video files.

This is system design in practice.

Functional vs Non-Functional Requirements

This is another very important concept in system design interviews.

Functional Requirements

These describe what the system should do.

For a food-delivery application:

User can register
User can log in
User can search restaurants
User can order food
User can make payments
User can track an order

These are functionalities.

Non-Functional Requirements

These describe how well the system should work.

Examples:

System should support 10 million users
Response should be under 200 ms
System should be highly available
Data should be secure
System should handle failures
System should scale as traffic increases

A useful memory trick:

Functional = What does the system do?
Non-functional = How well does it do it?

What Does a System Designer Actually Do?

A system designer generally asks questions like:

Step 1: What are we building?

For example:

"Design a food-delivery system."

Step 2: What should it do?
User
 ↓
Search restaurant
 ↓
Select food
 ↓
Place order
 ↓
Pay
 ↓
Track delivery

Step 3: How many users?

Maybe:

1 million users
10 million requests/day


The exact numbers influence architectural decisions.

Step 4: What data do we need?

For example:

User
Restaurant
Food
Order
Payment
Delivery

Step 5: Where should data be stored?

Choose appropriate databases and storage systems.

Step 6: How will we handle high traffic?

Consider:

Load Balancer
     ↓
Multiple Servers
     ↓
Cache
     ↓
Database

Step 7: What happens if something fails?

For example:

Server 1 ❌
    ↓
Server 2 ✅

Step 8: How do we make it secure?

Consider:

Authentication
Authorization
Encryption
Rate limiting
Secure APIs
System Design in One Picture

You can think of a typical modern application like this:

                         USERS
                           |
                           ↓
                    +-------------+
                    |    CDN      |
                    +-------------+
                           |
                           ↓
                    +-------------+
                    |Load Balancer|
                    +-------------+
                           |
             +-------------+-------------+
             |             |             |
             ↓             ↓             ↓
          Server 1      Server 2      Server 3
             |             |             |
             +-------------+-------------+
                           |
            +--------------+--------------+
            |              |              |
            ↓              ↓              ↓
         Cache         Database       Message Queue
                           |              |
                           ↓              ↓
                       Storage      Background Workers


This is high-level system design.

How to Learn System Design

A good learning sequence is:

Understand client-server architecture
Learn HTTP and APIs
Learn databases
Understand SQL vs NoSQL
Learn indexing
Learn caching
Learn load balancing
Learn horizontal vs vertical scaling
Learn replication
Learn sharding
Learn message queues
Learn CDN
Learn distributed systems
Learn consistency and availability
Learn fault tolerance
Practice designing real systems

Then practice questions such as:

Design a URL shortener
Design WhatsApp
Design YouTube
Design Instagram
Design an online shopping system
Design a food-delivery system
Design a ride-sharing system
Design a notification system
The Most Important Concepts to Remember

If you're a beginner, don't try to memorize dozens of technologies first.

Understand these concepts:

                    SYSTEM DESIGN
                         |
       +-----------------+-----------------+
       |                 |                 |
   Scalability       Availability       Reliability
       |                 |                 |
   Load Balancer      Replication       Failover
   Caching            Redundancy        Backups
   Sharding
       |
       +-----------------------------------+
       |
   Performance
       |
   Cache
   CDN
   Indexing
       |
       +-----------------------------------+
       |
    Data Storage
       |
   SQL / NoSQL
   Replication
   Sharding
       |
       +-----------------------------------+
       |
    Communication
       |
   REST APIs
   Message Queues
   Events

In one sentence

System Design is the process of deciding the architecture, components, data flow, storage, communication, scalability, security, and reliability of a software system before and while building it.

And the easiest distinction to remember is:

HLD → Big picture / architecture

LLD → Detailed implementation / classes and methods

System Design → Making the entire system work efficiently, reliably, securely, and at scale.
