
Consider a EV charging Infrastructure-

![Kafka BB](https://github.com/abhishek-gupta-108/SystemDesign/blob/main/images/KafkaBB.png)

```
User App
   │
   ▼
Booking Service (Producer)
   │
   ▼
Kafka Broker
   │
   ▼
Consumers
 - Billing Service
 - Notification Service
 - Analytics Service
```
## Building Blocks

#### Producers : The Booking Service backend would usually be the Kafka producer. When a user books a slot:
   - User clicks Book Slot.
   - Backend API processes request
   - **Backend publishes an event to Kafka**
      ```
      Example event:
      
      {
        "event_type": "slot_booked",
        "user_id": 8451,
        "station_id": "DEL-22",
        "slot_time": "2026-03-10T10:00",
        "duration": 30
      }
      ```
     **The producer is not the mobile app or user. The backend service that writes events to Kafka is the producer.**

      ```
      Example topic: charging-slot-events
      ```

#### **Kafka Brokers - ** - In Apache Kafka, a broker is simply a Kafka server (machines with hard disks) that stores, holds messages and serves producers and consumers. The events are the messages that flow through Kafka and are stored in brokers.
   Think of it like this:
      Producer → Broker → Consumer

  **The broker is the middle system that receives, stores, and delivers events.** In production you usually run multiple brokers for reliability.
    
  ```
    Kafka Cluster
     ├─ Broker 1
     ├─ Broker 2
     └─ Broker 3
    
    slot-bookings
       ├─ Partition 0 → Broker 1
       ├─ Partition 1 → Broker 2
       └─ Partition 2 → Broker 3
  ```

What they do?
1. Handles the storage, retrival and distribution of messages efficiently.
2. Every message flows through the broker ensuring reliable data delivery across consumers
3. Without Brokers managing large scale data streams would be chaotic and unstructured.
4. They act as a backbone to distributed messaging ensuring seamless communication b/w producers and consumers.

Each broker is a node in the Kafka cluster. These node communicate with each other maintaining a distributed system that supports large scale data streaming. This distributed design prevents **bottlecks** ensuring smooth data flow across multiple apps.

By distributing load across multiple nodes/brokers, kafka ensures **relaibility**  and **performace at scale**.

Brokers ensures seemless horizontal scaling. As data volume grows, additional brokers can be added to distribute messages across multiple nodes ensuring optimal performance. This **Elasticity** makes kafka powerful choice for Organisations handling dynamic and growing data loads.

Kakfa also provides high fault tolerance in case of broker failures maintaining **durability** and **system reliability**.

**Dynamic Membership**: Brokers can join or leave clusters without downtime. This flexibility ensure **high availability and system mantainence**.

Examples: Large scale companies use Kafka extensively.
1. **Netflix** has ~4000 brokers across 50 clusters serving a trillion messages dailing to keep your streaming experience seemless.
2. **Pinterest** serves 3Trillion messages/day at 50GB per second storing 1 Exabyte of data in AWS S3.
3. **Paypal** has 1500 brokers across 85 clusters serving 99.99% uptime for secure transactions across the globe.
4. **LinkedIn** runs with 1400 Brokers to power 1.4T messages/day. Kafka originated aat LinkedIn.


#### Organizing Your data Streams for efficient access
