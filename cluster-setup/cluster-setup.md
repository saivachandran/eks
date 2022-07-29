# create cluster
```
eksctl create cluster --name eksctl-test --nodegroup-name ng-default --node-type t3.micro --nodes 2
```
# view nodegroup status
```
eksctl get nodegroup --cluster=eksctl-test
```

# create cluster with configfile
```
eksctl create cluster --config-file=eksctl-create-cluster.yaml
```

# view cluster status
```
eksctl get cluster
```

# delete cluster
```
eksctl delete cluster --name eksctl-test
```

# scale nodegroup

```
eksctl scale nodegroup --cluster=demo-eks --nodes=4 --name=demoeks-nodes
```
# delete nodegroup
```

eksctl delete nodegroup \
  --cluster demo-eks \
  --region ap-south-1 \
  --name demoeks-nodes
```  
  
# create nodegroup
  
```
eksctl create nodegroup \
  --cluster my-cluster \
  --region region-code \
  --name my-mng \
  --node-type m5.large \
  --nodes 3 \
  --nodes-min 2 \
  --nodes-max 4 \
  --ssh-access \
  --ssh-public-key my-key
```
