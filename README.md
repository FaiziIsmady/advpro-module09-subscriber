### a. What is AMQP?

AMQP (Advanced Message Queuing Protocol) is an open communication protocol designed for reliable and structured message delivery between distributed systems or applications. It enables asynchronous communication, meaning that the sender and receiver do not need to interact with the message queue at the same time. AMQP is commonly used with message brokers like RabbitMQ, as it supports features such as message queues, exchanges, and flexible routing mechanisms. These capabilities make AMQP ideal for scalable and fault-tolerant system architectures.

### b. What does it mean? guest:guest@localhost:5672

The string guest:guest@localhost:5672 is part of a connection URL used to access a message broker that implements the AMQP protocol, such as RabbitMQ. The first guest refers to the username used for authentication, while the second guest is the corresponding password. localhost indicates that the broker is running on the local machine, and 5672 is the default port number that RabbitMQ uses for AMQP connections. This connection string allows a client application to connect to the RabbitMQ broker using the default credentials on the default local port.

### Simulation slow subscriber

![Image](https://github.com/user-attachments/assets/5b803f0d-70f3-4c6f-84a8-3937b91bc283)

To simulate a scenario where the subscriber is slow in processing messages, I uncommented the line `thread::sleep(ten_millis);` in the subscriber’s `main.rs` file. This introduces a 1-second delay for every message that is received and handled.

After rebuilding and running the subscriber, I ran the publisher multiple times in quick succession. As a result, RabbitMQ's message broker began to accumulate messages in its queue faster than the subscriber could consume them. This can be observed in the **"Queued messages"** chart on the RabbitMQ dashboard, where the message count temporarily increased before being gradually processed.

In my case, the total queued messages reached 20, which corresponds to the number of unprocessed messages during the time the subscriber was still handling previous ones. This behavior is similar to high-demand systems like SIAK during IRS registration, where many requests come in faster than the system can handle, resulting in delays or queue buildup.