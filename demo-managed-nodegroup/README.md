# Create the deployment:
```
kubectl apply -f nginx-deployment.yaml
```

# Verify that your pods are running and have their own internal IP addresses:
```
kubectl get pods -l 'app=nginx' -o wide | awk {'print $1" " $3 " " $6'} | column -t
```

# Create a LoadBalancer service

# Apply the loadbalancer.yaml file:

```
kubectl create -f loadbalancer.yaml
```


# Get information about nginx-service:
```
kubectl get service/nginx-service-loadbalancer |  awk {'print $1" " $2 " " $4 " 
```

[Refer link1](https://docs.aws.amazon.com/eks/latest/userguide/sample-deployment.html)

[Refer link2](https://docs.aws.amazon.com/eks/latest/userguide/sample-deployment.html)

[Rfer link3](https://aws.amazon.com/premiumsupport/knowledge-center/eks-access-kubernetes-services/)


# create Managed nodegroup
```
eksctl create cluster --name demo-eks --nodegroup-name demoeks-nodes --node-type t3.micro --nodes 4  --managed

```

# deploy sample nginx application

```
 kubectl apply -f nginx-deployment.yaml
  
 kubectl apply -f loadbalancer.yaml
 
``` 
