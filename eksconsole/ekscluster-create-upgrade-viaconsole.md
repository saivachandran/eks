**create cluster iam role:**
**create dedicated vpc using cloudformation template:**
**create eks cluster:**
**install iam auth amd kubectls on working instance:**

kubeconfig update
---------------
```
aws eks --region ap-south-1 update-kubeconfig --name eks-demo-cluster
export KUBECONFIG=~/.kube/config

```

5. create role for worker node
   policy: ekscni,workernodepolicy,ec2contaierread

 6. create worker node
 7. deploy sample app

[refer video](https://www.youtube.com/watch?v=aZd0UolVwD4)
