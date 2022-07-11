# create cluster

eksctl create cluster --name eksctl-test --nodegroup-name ng-default --node-type t3.micro --nodes 2

# view nodegroup status

eksctl get nodegroup --cluster=eksctl-test


# create cluster with configfile

eksctl create cluster --config-file=eksctl-create-cluster.yaml


# view cluster status

eksctl get cluster


# delete cluster

eksctl delete cluster --name eksctl-test
