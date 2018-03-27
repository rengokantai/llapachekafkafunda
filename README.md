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
