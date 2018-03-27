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
