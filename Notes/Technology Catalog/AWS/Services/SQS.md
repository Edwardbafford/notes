Standard Queue Service

Managed queue

Use **access policies** to control access

## Features

Producers send messages

Messages are retained by SQS but eventually deleted. Retention time is configurable.

Consumers poll SQS for messages. While polling consumers can wait a configurable amount of time for a message before ending the poll.

After being read a message is invisible for a configurable amount of time.

Once a message has been processed by a consumer it should be deleted.



## FIFO Queue

Special queue with limited performance 

Perserves message order and doesn't allow for duplicates



