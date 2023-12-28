kubernetes cluster version upgrade
----------------------------------

step1 : upgrade controlplane components

```
kubectl get nodes

```

NAME                                            STATUS   ROLES    AGE     VERSION
ip-192-168-21-144.ap-south-1.compute.internal   Ready    <none>   7m8s    v1.23.17-eks-e71965b
ip-192-168-62-95.ap-south-1.compute.internal    Ready    <none>   7m18s   v1.23.17-eks-e71965b

```
eksctl get cluster

```

NAME            REGION          EKSCTL CREATED
spot-cluster    ap-south-1      True



check upgrade verion without approve command
--------------------------------------------
```
eksctl upgrade cluster --name=spot-cluster

```
 
2023-12-28 06:01:59 [ℹ]  (plan) would upgrade cluster "spot-cluster" control plane from current version "1.23" to "1.24"
2023-12-28 06:01:59 [ℹ]  re-building cluster stack "eksctl-spot-cluster-cluster"
2023-12-28 06:01:59 [✔]  all resources in cluster stack "eksctl-spot-cluster-cluster" are up-to-date
2023-12-28 06:01:59 [ℹ]  checking security group configuration for all nodegroups
2023-12-28 06:01:59 [ℹ]  all nodegroups have up-to-date cloudformation templates
2023-12-28 06:01:59 [!]  no changes were applied, run again with '--approve' to apply the changes


```

eksctl upgrade cluster --name=spot-cluster --approve
```


step2: update daemonsets
=======================
```
eksctl utils update-kube-proxy --cluster=spot-cluster --approve

```
```
eksctl utils update-coredns --cluster=spot-cluster --approve

```

verify update
============
```
 kubectl get daemonset kube-proxy --namespace kube-system -o=jsonpath='{$.spec.template.spec.containers[:1].image}'
 
 kubectl describe deployment coredns --namespace kube-system | grep Image | cut -d "/" -f 3

```




step2: update managed nodegroup
------------------------------

two nodegroups
-------------

```
eksctl upgrade nodegroup --name=spot --cluster=spot-cluster --kubernetes-version=1.24

```


```
eksctl upgrade nodegroup --name=on-demand --cluster=spot-cluster --kubernetes-version=1.24

````

View upgrade version
===================
```
kubectl get nodes --watch

```

[eksupgrade referlink](https://archive.eksworkshop.com/intermediate/320_eks_upgrades/upgrademng/)

