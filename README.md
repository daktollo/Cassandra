# Cassandra
Installing Cassandra

## 1-Download the Docker Cassandra Image

Open the terminal and pull the Cassandra image:

```shell
docker pull cassandra
```

## 2- Create a Docker Compose File

Configure Cassandra by specifying the following ports:

```shell
version: '3'
services:
  cassandra:
    image: cassandra:latest
    ports:
      - "24485:7000"   # Cassandra inter-node communication
      - "24486:7001"   # Cassandra JMX port
      - "24487:7199"   # Cassandra JMX remote port
      - "24488:9042"   # Cassandra CQL native transport
      - "24489:9160"   # Cassandra Thrift RPC
    volumes:
      - cassandra-data:/var/lib/cassandra
    networks:
      - cassandra-net

volumes:
  cassandra-data:

networks:
  cassandra-net:
    driver: bridge
```

## 3- Start the Cassandra Container

Launch the Cassandra container in the background:

```shell
docker-compose up -d
```


## 4- Connect to the Cassandra Container

Access the Cassandra shell using the following command:

```shell
docker-compose exec cassandra bash
```

```shell
cqlsh
```

## 5- Stop Cassandra

To stop Cassandra, run the following command:

```shell
docker-compose down
```
