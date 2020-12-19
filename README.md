# poc_kafka

## Montagem do cluster

Clonar o repositório: 
- **https://github.com/confluentinc/cp-docker-images**
Na pasta "exemples" existem diversas formas de montar o server do kafka. 

Utilizei o exemplo de montagem do cluster: 
- **https://github.com/confluentinc/cp-docker-images/blob/5.3.3-post/examples/kafka-cluster/docker-compose.yml**
Subir o servidor utilizando o **docker-compose up -d**

Entrar dentro do conteiner docker: 
- **docker exec -it kafka-cluster_kafka-1_1 bash**

## Criação do tópico

Criar um tópico: 
-  **kafka-topics --create --bootstrap-server localhost:29092 --replication-factor 3 --partitions 3 --topic meutopico**

Listar os tópicos:
-  **kafka-topics --list --bootstrap-server localhost:29092**

## Simulando um producer
- **kafka-console-producer --broker-list localhost:29092 --topic meutopico**

## Simulando um consumer

- **kafka-console-consumer --bootstrap-server localhost:29092 --topic meutopico**
- **kafka-console-consumer --bootstrap-server localhost:29092 --topic meutopico --from-beginning** 
- **kafka-console-consumer --bootstrap-server localhost:29092 --topic meutopico --from-beginning --group a**

## Describe nos tópicos
- **kafka-topics --describe --bootstrap-server localhost:29092 --topic meutopico**
- **kafka-consumer-groups --group a --bootstrap-server localhost:29092 --describe**