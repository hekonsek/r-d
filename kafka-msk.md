# Apache Kafka with AWS MSK

[AWS MSK](https://aws.amazon.com/msk) (Managed Streaming Kafka) is a managed Apache Kafka service provided by AWS - you can think of it like of Kafka broker as a service.

## What is it useful for?

MSK is useful if you would like to use Kafka cluster, but you don't want to manage it by yourself. The typical use case is when you don't have Kafka operational expertise within your organization - you pay Amazon to provision and operate Kafka cluster for you.

## Creating minimal cluster

For development purposes it usually makes no sense to create large and expensive cluster. Primary reason for that is your development environments usualy don't require high message throughput due to the limited traffic volume. Secondary reason is lower HA (High Availability) and data redundancy level expected from non-production environments.

Let's start our MSK exploration with a CloudFormation template which creates the simplest and the smallest Apache Kafka cluster. 

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

In order to create new MSK Kafka cluster execute the following AWS CLI command:

```
$ vim msk.yml # Save Cloud Formation template from above
$ aws cloudformation create-stack --stack-name mykafkacluster --template-body `cat msk.yml`
```
