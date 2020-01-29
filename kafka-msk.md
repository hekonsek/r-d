# Apache Kafka with AWS MSK

## Creating minimal cluster

For development purposes it makes now sense to create large and expensive cluster. Let's start our MSK exploration with a CloudFormation template which creates the simplest and the smallest Apache Kafka cluster. 

```
Resources:
  KafkaCluster:
    Type: AWS::MSK::Cluster
    Properties:
      ClusterName: MyCluster
      KafkaVersion: 2.3.1
      NumberOfBrokerNodes: 2
      BrokerNodeGroupInfo:
        InstanceType: kafka.m5.large
        ClientSubnets:
          - subnet-62623c3f
          - subnet-bf1449d9
```                                        

