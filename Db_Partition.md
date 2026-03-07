

## Q) When is DB partitioning required?

          You shard when one machine cannot handle:
          | Reason           | Example                     |
          | ---------------- | --------------------------- |
          | Write throughput | too many writes/sec         |
          | Read throughput  | too many reads/sec          |
          | Data size        | dataset larger than machine |
          
          **So sharding solves capacity limits.**
          
          #### When Reads Are High
          
          If reads are high, the first solution is usually caching, not sharding.
          DB
          │
          ▼
          Redis Cache
          
          Because:
          1. Cache handles millions of reads/sec
          2. DB gets very few reads
          
          ### When Read Load Still Becomes Huge
          
          If reads are still very large, **then we use read replicas before sharding.**<br>
          
          Architecture:<br>
                    ┌────────────┐
                    │   Master   │
                    │   (writes) │
                    └─────┬──────┘
                          │
                  ┌───────┴────────┐
                  ▼                ▼
             Read Replica      Read Replica
          
          
          Benefits:
          
          Scale reads
          
          Simple architecture
          
          Example:
          
          1 write node
          10 read replicas
          
          ### When Even Replicas Are Not Enough
          
          Then we use sharding.
          
          Example:
          
          Shard 1 → posts 1–1M
          Shard 2 → posts 1M–2M
          Shard 3 → posts 2M–3M
          
          Each shard can also have its own read replicas.
          
          Shard 1
            ├─ master
            ├─ replica
            └─ replica
          
          Shard 2
            ├─ master
            └─ replica
          
          **This scales reads and writes.**
          
