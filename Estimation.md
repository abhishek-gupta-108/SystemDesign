
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
