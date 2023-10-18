
Concurrency is used to increase a systems performance.

Overhead is involved in dividing tasks and recombining them which results in diminishing returns as the number of threads or processes increases.

Design factors
- Safety - ensuring system consistency
- Liveness - preventing deadlocks or stuck systems
- Performance
- Ease of use

Deadlocks can be prevented by ensuring locks are acquired in the same order by all threads.

Using immutable objects is a good way to help ensure consistency.
