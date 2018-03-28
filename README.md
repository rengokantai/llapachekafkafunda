# llapachekafkafunda

## 7 Writing Producers
### Producer Configuration
List of host/port pairs
- Host is the system that has broker running
- Post is the port number broker is listening on
- Only one host/port is required
- Recommended at least two in case one broker is unreachable
```
bootstrap.servers, "localhost:9091,localhost:9092"
```

Serializers
- messages are collections of keys and values
- kafka makes use of byte arrays
- producer can use any java object for key and value

  
key.serializer and value.serializer
- key.serializer: How to serialize the key
- value.serializer: How to serialize the value
- Can be different
- Example:
```
"key.serializer":"org.apache.kafka.common.serialization.StringSerializer"
```

Additional Configurations
- acks
- buffer.memory
- retries
- batch.size


### 2 Constructing Producers
Two key configurations affect batching
- batch.size
- linger.ms

acks settings
###### 0 
- High throughput
- Low latency
- Message loss could occur
###### 1
- Medium throughput
- Medium latency
- Message loss rare
###### all or -1
- Low throughput
- High latency
- Message loss very rare


### 3 Communicating with Kafka
Three methods to send messages
- Simple send
- Synchronous send
- Asynchronous send

Simple
```
ProducerRecord<String,String> record = new ProducerRecord<>();
try {
  producer.send(record).get();
} catch(Exception e){
  e.printStackTrace();
}
```



### 5 Partitions
Review
- If there is only one Kafka Broker, partitions dont come into play
- If there are multiple Brokers, the data sent to a topic can be placed and/or replicated on several Brokers
- Each instance of the data called a partition
- Each consumer keeps track of what messages it has read by a numbric value that represents an Offset


## 8 Writing Consumers
### 2 Consumer Groups
Advantages of multiple consumer groups
- Single consumer can be overwhelmed
- Allows for scaling based on data load

Disadvantages of multiple consumer groups
- Order guarantee may be more complex to deal with
- Could result in partition rebalance issues


Partition Rebalance
- First consumer acts as leader
- Assigned partitions to each new consumer
- Partition Rebalance is when assignments must be changed:
  - When new consumer is added
  - When a consumer is removed or crashes
- Rebalance results in a short window when consumers are not consuming data
