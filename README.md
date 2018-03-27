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


#### Serializers
note
- messages are collections of keys and values
- kafka makes use of byte arrays
- producer can use any java object for key and value
