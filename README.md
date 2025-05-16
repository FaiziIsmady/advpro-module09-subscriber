### a. What is AMQP?

AMQP (Advanced Message Queuing Protocol) is an open communication protocol designed for reliable and structured message delivery between distributed systems or applications. It enables asynchronous communication, meaning that the sender and receiver do not need to interact with the message queue at the same time. AMQP is commonly used with message brokers like RabbitMQ, as it supports features such as message queues, exchanges, and flexible routing mechanisms. These capabilities make AMQP ideal for scalable and fault-tolerant system architectures.

### b. What does it mean? guest:guest@localhost:5672

The string guest:guest@localhost:5672 is part of a connection URL used to access a message broker that implements the AMQP protocol, such as RabbitMQ. The first guest refers to the username used for authentication, while the second guest is the corresponding password. localhost indicates that the broker is running on the local machine, and 5672 is the default port number that RabbitMQ uses for AMQP connections. This connection string allows a client application to connect to the RabbitMQ broker using the default credentials on the default local port.