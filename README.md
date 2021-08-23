# Spring Boot Messaging Sample in Kafka Container

Simple Spring Boot App to publish & consume messages with docker compose config to run kafka / zookeeper in containers

## Quick Steps
1. Clone from git repo
   ```
   git clone https://github.com/kcheung00/kafka_app.git
   ```
2. Navigate to kafka_image folder contains docker-compose.yml file
   ```sh
   cd kafka_app/kafka_image
   ```
3. Ensure KAFKA_ADVERTISED_LISTENERS has the local machine IP address. Refer to the Note section for detail.
   ```
   ex. KAFKA_ADVERTISED_LISTENERS: INSIDE://kafka:9093,OUTSIDE://192.168.1.65:9096
   ```
4. Start the Kafka / Zookeeper container (cd kafka_image)
   ```sh
   docker-compose -f docker-compose.yml -d
   ```
5. Build the App (cd kafka_app)
   ```sh
   mvn clean install
   ```
6. Execute the App
   ```
   mvn spring-boot:run
   ```
7. Stop the App
   ```
   Control C
   ```
8. Stop the container without delete the container
   ```
   docker-compose stop
   ```
   OR

   Stop and delete container
   ```
   docker-compose down
   ```


## Notes
In docker-compose.yml, replace `YOUR_BROKER_HOST_PUBLIC_IP` with local machine IP address:
```sh
KAFKA_ADVERTISED_LISTENERS: INSIDE://kafka:9093,OUTSIDE://YOUR_BROKER_HOST_PUBLIC_IP:9092
```

### Avaliable console params 

* ***- - consumer-enabled*** - you can disable/enable consumer if needed. Default is true
* ***- -kafka_bootstrap_servers*** - set your server address here to call kafka from external hosts. Default is localhost:9092
* ***- -kafka_username / --kafka_password*** - you can change default user in kafka_conf/kafka_server_jaas.conf. Default is admin/admin-secret