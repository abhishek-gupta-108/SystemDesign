
#### Like Post on Social Media



## API Design:


## Key Bottlenecks:
1. Handling Hot posts - Celebrity posts can receive millions of likes per minute.
2. Idempotency : User may click like multiple times.
3. Eventual Consistency: DB write succeeds , Redis update fails
4. Rate Limiting: Prevent spam likes.
5. Like Count Problem: Computing count by querying table: COUNT(*) is slow


## Improvements:
    1. Batch Writes : Reduce DB pressure.
    2. Async Counters: Update counts asynchronously.
    3. Precomputed aggregates : For news feed rendering.
