
Managed system for capturing, storing, and processing stream data.

Data stored is immutable.

Data can be processed multiple times.


## Shards

Storage consists of shards.

Each shard keeps the data in order.

Partition Key hashes to a shard.


## Modes

Provisioned - choose shards which hit read/write limit

On-demand - # of shards scale to meet demand