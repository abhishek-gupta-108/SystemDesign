
## User Scale

| Platform       | Users |
| -------------- | ----- |
| Startup        | 1M    |
| Mid product    | 10M   |
| Large product  | 100M  |
| Facebook scale | 1B    |


## Data Sizes

| Data         | Size      |
| ------------ | --------- |
| ID           | 8 bytes   |
| Timestamp    | 8 bytes   |
| Small object | 100 bytes |
| Image        | 1 MB      |
| Video minute | 5–10 MB   |


## Traffic Estimation Trick
Use this formula:

Requests/sec = (DAU × actions per day) / 100,000 ( 1 day ≈ 100,000 seconds : actual 86400 but round)

## Storage Estimation Trick
Formula:

Storage = events/day × object_size

## Read Traffic Trick

Reads are usually **10–100× writes.**

So if writes:

**60K/sec**

Reads:

**600K – 6M/sec**

This immediately tells interviewer:
1. need cache
2. need CDN
3. need sharding


## Peak Traffic Rule (Think in QPS)
Peak traffic is usually: **3–10× average**

So if: **50K/sec**

Peak: **250K/sec**

## Partitioning Rule

When QPS exceeds: **10K–20K writes/sec**

Single database becomes risky.

So you say: **"We'll shard by post_id."**

## Cache Size Trick
Example:
Assume: **1B posts**

Each cached like counter:
**post_id = 8B
count = 8B**

**16 bytes**

Total:

**1B × 16B
= 16GB**

This fits in **Redis cluster.**

# SIZE/SPEED Estimates

### SATA SSD :
A SATA SSD (Solid State Drive) is a type of storage drive that uses the common Serial ATA (SATA) interface, offering significant speed improvements over traditional hard drives (HDDs) by using flash memory instead of spinning platters, making computers boot faster and applications load quicker, though it's slower than newer NVMe SSDs.

### An NVMe SSD:
is a high-performance Solid-State Drive that uses the Non-Volatile Memory Express (NVMe) protocol, connecting directly to the CPU via the PCI Express (PCIe) bus for dramatically faster data transfer, lower latency, and higher input/output operations per second (IOPS) compared to older SATA-based SSDs. It's built specifically for flash memory, enabling lightning-fast speeds for gaming, large file transfers, and demanding applications like AI and video editing

### Typical Disk Size per Server (Production Systems)

Modern backend servers usually have NVMe SSDs.

**Typical configurations:**

| Storage Type          | Typical Size |
| --------------------- | ------------ |
| SATA SSD              | 1–4 TB       |
| NVMe SSD              | 2–8 TB       |
| High-end storage node | 8–16 TB      |
| Cold storage node     | 20–100 TB    |


**A common assumption in interviews: 1 machine ≈ 4–8 TB usable storage**

But remember:
**Replication reduces usable storage.**<br>

```
  Example:
  8 TB disk
  3× replication
  usable ≈ 2.6 TB
  
```
**Distributed DBs like Cassandra, DynamoDB, HBase replicate data.**


### Typical Disk Speed

For databases the important metric is IOPS and throughput.

**HDD (old systems)**

| Metric     | Value    |
| ---------- | -------- |
| IOPS       | 100–200  |
| Throughput | 150 MB/s |

Not used for high-traffic DBs anymore.

**SATA SSD**
| Metric     | Value    |
| ---------- | -------- |
| IOPS       | 50K–100K |
| Throughput | 500 MB/s |


**NVMe SSD (modern servers)**
| Metric     | Value    |
| ---------- | -------- |
| IOPS       | 500K–1M  |
| Throughput | 3–7 GB/s |

**This is why modern distributed databases scale well.**




### Typical Database Throughput

Now let's talk about queries per second.<br>

These are ballpark engineering numbers.

**SQL Databases (MySQL / PostgreSQL)**

Single node capacity roughly:

| Operation | Typical QPS |
| --------- | ----------- |
| Reads     | 10K–50K/sec |
| Writes    | 5K–20K/sec  |


With tuning and replication:

Reads can scale to 100K+/sec

Why writes are slower:

1. transactions
2. locks
3. indexes
4. WAL logging

**NoSQL Databases (Cassandra / DynamoDB / HBase)**

These are optimized for horizontal scaling and high writes. Per node:

| Operation | Typical QPS  |
| --------- | ------------ |
| Reads     | 50K–200K/sec |
| Writes    | 20K–100K/sec |


Key reasons:
1. no joins
2. append-heavy design
3. LSM trees

Example:

**Cassandra clusters** can easily handle: **millions of writes/sec** with enough nodes.


### Typical Redis Node Size

Redis stores data in RAM, so size depends on memory.

Common production nodes:
| RAM        | Usage          |
| ---------- | -------------- |
| 16 GB      | small services |
| 32 GB      | common         |
| 64 GB      | large cache    |
| 128–256 GB | heavy systems  |

**Typical assumption: Redis node ≈ 64 GB RAM**

Companies use Redis clusters.
Example:

10 nodes × 64 GB
≈ 640 GB cache

### Redis Throughput

Redis is extremely fast.

Single node:
| Operation | Throughput |
| --------- | ---------- |
| Reads     | 1M+/sec    |
| Writes    | 500K+/sec  |

**Latency : ~0.1–1 ms**

That's why Redis is used for:
1. counters
2. session storage
3. hot data

### Network Bandwidth (Often Forgotten)

Typical server NICs:
| Type             | Speed    |
| ---------------- | -------- |
| Standard         | 10 Gbps  |
| High-performance | 25 Gbps  |
| Very high-end    | 100 Gbps |

10 Gbps means:

≈ 1.25 GB/sec

Network often becomes bottleneck before disk.

## Practical Interview Numbers (Memorize These)

If you're stuck in a system design interview, use these:
```
Single SQL node
  reads ≈ 20K/sec
  writes ≈ 10K/sec
```
```  
NoSQL node
  reads ≈ 100K/sec
  writes ≈ 50K/sec
```
```
Redis node
  ops ≈ 1M/sec
Server storage
  ≈ 4–8 TB
```
```
Redis memory
  ≈ 64 GB
```

These are perfectly acceptable interview assumptions.


#### The Key Insight Senior Engineers Use

They never depend on one machine.

Instead they think:

capacity per node
×
number of nodes
=
system capacity

Example:

50K writes/sec per node
20 nodes
= 1M writes/sec capacity
