# Basics 
broker.id=1.

num.network.threads=4.

num.io.threads=8.

socket.send.buffer.bytes=102400.

socket.receive.buffer.bytes=102400.

socket.request.max.bytes=104857600.

max.connections.per.ip=20.

message.max.bytes=15728640.

num.partitions=3.

num.recovery.threads.per.data.dir=2.

#queued.max.requests= .


# Memory Configuration
heap.opts=-Xmx4G -Xms4G.  

# Log Configuration
log.dirs=C:/kafka-01/log-01.  
log.segment.bytes=536870912.  
log.flush.interval.ms=10000.  
log.flush.interval.messages=100000.  
log.retention.bytes=-1.  
log.retention.hours=48.  
log.cleaner.enable=true.  
log.cleaner.threads=2.  
log.cleaner.dedupe.buffer.size=134217728.  
log.cleaner.io.buffer.size=524288.  
log.cleaner.backoff.ms=15000.  
log.cleaner.min.cleanable.ratio=0.5.  
log.cleaner.delete.retention.ms=86400000.  
log.cleanup.policy=delete.  
log.retention.check.interval.ms=300000.  

# Replication Configuration
default.replication.factor=2.
min.insync.replicas=2.
replica.lag.time.max.ms=60000.
replica.fetch.max.bytes=15728640.

# Compression Configuration
compression.type=snappy.

# Network Configuration
listeners=PLAINTEXT://192.168.1.238:9092.
advertised.listeners=PLAINTEXT://192.168.1.238:9092,PLAINTEXT://192.168.1.236:9092,PLAINTEXT://192.168.1.165:9092.

# Delete Topic Configuration
delete.topic.enable=true.

# Internal Topic Settings
offsets.topic.replication.factor=2.
transaction.state.log.replication.factor=2.
transaction.state.log.min.isr=2.

# Group Coordinator Settings
group.initial.rebalance.delay.ms=0.

# Zookeeper
zookeeper.connect=192.168.1.238:2181.
zookeeper.connection.timeout.ms=18000.

