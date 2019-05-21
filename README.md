# kafka_consumer_group_exporter_helm_charts
Helm chart for kafka_consumer_group_exporter

## Usage

Configure the value.yml

| key  | default value  | comment  |
|---|---|---|
|  replicaCount | 1  | number of pods   |
| image.repository  | ianitrix/kafka-consumer-group-exporter  | docker image name |
| image.tag  | v0.0.2  | docker image tag |
| image.pullPolicy  | IfNotPresent  | docker image pull policy |
| imagePullSecrets  |   |   |
| nameOverride  |   |   |
| fullnameOverride  |   |   |
| service.enabled  |  true | enable the k8s service  |
| service.port  | 80  |  port of the k8s service |
| prometheus.enabled  | true  | add default annotations to be scraped by prometheus |
| configuration.*  |   |  Kafka Admin client configuration
# See https://kafka.apache.org/documentation/#adminclientconfigs |
| configuration.bootstrap.servers  |  my-confluent-oss-cp-kafka:9092 |  kafka bootstrap servers |


Then start with

```bash
helm repo add ianitrix https://github.com/GuillaumeWaignier/kafka_consumer_group_exporter_helm_charts/kafka-consumer-group-exporter/
helm repo update
helm install ianitrix/kafka-consumer-group-exporter --name exporter
```

## Example

1. Deploy kafka

```bash
helm repo add confluentinc https://confluentinc.github.io/cp-helm-charts/
helm repo update
helm install confluentinc/cp-helm-charts --name my-confluent-oss
```

2. Configure the exporter

```properties
bootstrap.servers: my-confluent-oss-cp-kafka:9092
```

3. Deploy the kafka_consumer_group_exporter

```bash
helm repo add ianitrix https://github.com/GuillaumeWaignier/kafka_consumer_group_exporter_helm_charts/kafka-consumer-group-exporter/
helm repo update
helm install ianitrix/kafka-consumer-group-exporter --name exporter
```
