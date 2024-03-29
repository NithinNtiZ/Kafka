# LOG CONFIGURATION

- `**log.dirs:**` -This setting specifies the directories in which the Kafka broker will store its log files. You can specify multiple directories by separating them with commas.

- `**log.retention.hours:**` This setting specifies the number of hours for which log files will be retained. Once this time has passed, log files will be deleted.

- `**log.retention.bytes:**` This setting specifies the maximum size of all log segments in a topic partition. Once the total size of all log segments in a partition exceeds this value, the oldest segment will be deleted to make room for new data.

- `**log.retention.ms:**` This setting specifies the number of milliseconds for which log files will be retained. Once this time has passed, log files will be deleted.

- `**log.segment.bytes:**` This setting specifies the size of the log segments in bytes. Once a log segment reaches this size, it will be closed and a new one will be created.

- `**log.segment.ms:**` This setting specifies the time interval for rolling new log segments in milliseconds.

- `**log.flush.interval.ms:**` This setting specifies the maximum time in milliseconds between log flushes..

- `**log.flush.offset.checkpoint.interval.ms:**` This setting specifies the time interval between offset checkpoints in milliseconds.

- `**log.flush.scheduler.interval.ms:**` This setting controls the interval at which log flusher thread wakes up to flush logs.

- `**log.cleaner.enable:**` This setting enables or disables the log cleaner. The log cleaner is a background thread that runs in the broker and is responsible for deleting old log files.

- `**log.cleaner.threads:**` This setting specifies the number of cleaner threads to run in the broker.

- `**log.cleaner.dedupe.buffer.size:**` This setting specifies the size of the buffer to use for deduplication in bytes.

- `**log.cleaner.io.buffer.size:**` This setting specifies the size of the I/O buffer to use in bytes.

- `**log.cleaner.io.max.bytes.per.second:**` This setting specifies the maximum I/O rate that the cleaner can sustain in bytes per second.

- `**log.cleaner.backoff.ms:**` This setting specifies the amount of time to wait before retrying a failed log cleaner task.

- `**log.cleaner.min.cleanable.ratio:**` This setting specifies the minimum ratio of bytes that can be cleaned to the total log size for a log to be eligible for cleaning.

- `**log.cleanup.policy:**` This setting specifies the log cleanup policy that should be used. The available options are "delete" and "compact".
---

# NETWORK CONFIGURATION   

- `**listeners:**` This setting specifies the network interfaces and ports that the Kafka broker should listen on for connections. The format is "listener_name://host:port"

- `**advertised.listeners:**` This setting specifies the network interfaces and ports that the Kafka broker will advertise to clients. The format is "listener_name://host:port"

- `**inter.broker.listener.name:**` This setting specifies the listener to use for inter-broker communication.

- `**num.network.threads:**` This setting specifies the number of threads to use for network processing.

- `**num.io.threads:**` This setting specifies the number of threads to use for I/O operations.

- `**socket.send.buffer.bytes:**` This setting specifies the size of the send buffer to use for socket connections in bytes.

- `**socket.receive.buffer.bytes:**` This setting specifies the size of the receive buffer to use for socket connections in bytes.

- `**socket.request.max.bytes:**` This setting specifies the maximum size of a request that the Kafka broker will accept.

- `**queued.max.requests:**` This setting specifies the maximum number of requests that can be queued for network threads to process.

- `**connections.max.idle.ms:**` This setting specifies the maximum time in milliseconds that a connection can be idle before it is closed.

- `**max.connections.per.ip:**` This setting specifies the maximum number of connections that can be made to the broker from a single IP address.

- `**max.connections.per.ip.overrides:**` This setting overrides the max.connections.per.ip setting for specific IP addresses or IP ranges.

- `**security.inter.broker.protocol:**` This setting specifies the security protocol to use for inter-broker communication.

- `**ssl.keystore.location:**` This setting specifies the location of the keystore file to use for SSL/TLS connections.

- `**ssl.keystore.password:**` This setting specifies the password for the keystore file.

- `**ssl.key.password:**` This setting specifies the password for the key in the keystore file.

- `**ssl.truststore.location:**` This setting specifies the location of the truststore file to use for SSL/TLS connections.

- `**ssl.truststore.password:**` This setting specifies the password for the truststore file.

# OTHER

`**fetch.max.wait.ms**` specifies the maximum amount of time (in milliseconds) that a Kafka broker will wait for additional messages to arrive from the producer before returning a response to the consumer. A higher value for fetch.max.wait.ms can reduce the number of requests made by the consumer to the Kafka broker, but it also means that there may be a longer delay in processing new messages. The default value for fetch.max.wait.ms is 500 milliseconds.   
`**max.poll.interval.ms**` specifies the maximum amount of time (in milliseconds) that a consumer is allowed to go without making a call to the Kafka broker to fetch new messages. This is a safety mechanism to prevent long-running consumers from holding on to Kafka partitions for too long without processing any messages. If a consumer exceeds the max.poll.interval.ms time limit without fetching new messages, it will be considered failed and removed from the group. The default value for max.poll.interval.ms is 300000 milliseconds (5 minutes).

Both fetch.max.wait.ms and max.poll.interval.ms can be configured to optimize the trade-off between responsiveness and efficiency for a given use case. For example, if low latency is critical for your application, you may want to reduce the value of fetch.max.wait.ms to ensure that messages are processed as quickly as possible. On the other hand, if you have a large number of consumers or a high volume of messages, you may want to increase the value of max.poll.interval.ms to avoid excessive rebalancing and partition assignment.



---

# EXAMPLE

 
 - `**listeners:**` should be set to "PLAINTEXT://:9092" or "PLAINTEXT://your_host_name:9092"

- `**advertised.listeners:**` should be set to the externally reachable hostname or IP address of the broker, for example, "PLAINTEXT://your_public_host_name:9092"

- `**inter.broker.listener.name:**` should be set to "PLAINTEXT"

- `**num.network.threads:**` should be set to at least the number of cores on the server

- `**num.io.threads:**` should be set to at least the number of cores on the server

- `**socket.send.buffer.bytes:**` should be set to a value that is larger than the maximum message size produced by clients

- `**socket.receive.buffer.bytes:**` should be set to a value that is larger than the maximum message size produced by clients

- `**socket.request.max.bytes:**` should be set to a value that is larger than the maximum message size produced by clients

- `**queued.max.requests:**` should be set to a value that is larger than the number of clients that will be connecting to the cluster

- `**connections.max.idle.ms:**` should be set to a value that is smaller than the time it takes for clients to reconnect after a connection is closed

- `**max.connections.per.ip:**` should be set to a value that is larger than the number of clients that will be connecting to the cluster from a single IP address

- `**ax.connections.per.ip.overrides:**` should be set to a value that is larger than the number of clients that will be connecting to the cluster from a single IP address

- `**security.inter.broker.protocol:**` should be set to "PLAINTEXT" if you are not using any security protocol


---


- `**message.timestamp.difference.max.ms**` is a configuration parameter in Apache Kafka that specifies the maximum difference allowed between the timestamp of a message and the broker's system time. When a message is produced to a Kafka topic, it is assigned a timestamp, which represents the time that the message was generated.

The `message.timestamp.difference.max.ms` setting is used to enforce the validity of timestamps in messages, as timestamps that are too far in the future or in the past are considered to be invalid. If a message has a timestamp that exceeds the "message.timestamp.difference.max.ms" value, the message will be rejected by the broker.

This setting is used to help ensure the consistency and accuracy of message timestamps in Apache Kafka, and it should be set based on your specific requirements for timestamp accuracy and the expected clock skew between your producers and brokers.
---
Compression ratio: The compression ratio is the amount by which the size of the message is reduced after compression. Some compression algorithms, such as GZIP, provide higher compression ratios but may be slower than other algorithms. Other algorithms, such as Snappy, provide lower compression ratios but are faster.

Compression speed: The compression speed is the time it takes to compress the message. Some algorithms, such as LZ4, are very fast but may not provide as high a compression ratio as other algorithms.

Decompression speed: The decompression speed is the time it takes to decompress the message. Some algorithms, such as Snappy and LZ4, are very fast and can provide high decompression speeds.

CPU usage: The compression and decompression process can be CPU-intensive, so it's important to consider the available CPU resources when choosing a compression algorithm.