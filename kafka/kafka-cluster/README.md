```
kubectl apply -f controller.yaml -f broker.yaml  -f kafka-cluster.yaml 
```

output 
```
kafkanodepool.kafka.strimzi.io/controller created
kafkanodepool.kafka.strimzi.io/broker created
kafka.kafka.strimzi.io/kafka-cluster created
```



```
kubectl wait kafka/kafka-cluster --for=condition=Ready --timeout=300s -n kafka-system
```

Expected

```
NAME                                           READY   STATUS    RESTARTS   AGE
kafka-cluster-broker-3                         1/1     Running   0          2m
kafka-cluster-broker-4                         1/1     Running   0          2m
kafka-cluster-broker-5                         1/1     Running   0          2m
kafka-cluster-controller-0                     1/1     Running   0          2m
kafka-cluster-entity-operator-xxxxxxxxxx-xxxxx 2/2     Running   0          1m
strimzi-cluster-operator-xxxxxxxxxx-xxxxx      1/1     Running   0          6m
```
