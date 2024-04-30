
create cluster autoscaler
------------------------

Refer: https://github.com/awsdocs/amazon-eks-user-guide/blob/9780d74ec6b5928c47ce6eb0c4592c150d7754ad/doc_source/autoscaling.md

step-1: create policy
---------------------


AmazonEKSClusterAutoscaler
```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "VisualEditor0",
            "Effect": "Allow",
            "Action": [
                "autoscaling:SetDesiredCapacity",
                "autoscaling:TerminateInstanceInAutoScalingGroup"
            ],
            "Resource": "*",
            "Condition": {
                "StringEquals": {
                    "aws:ResourceTag/k8s.io/cluster-autoscaler/my-cluster": "owned"
                }
            }
        },
        {
            "Sid": "VisualEditor1",
            "Effect": "Allow",
            "Action": [
                "autoscaling:DescribeAutoScalingInstances",
                "autoscaling:DescribeAutoScalingGroups",
                "ec2:DescribeLaunchTemplateVersions",
                "autoscaling:DescribeTags",
                "autoscaling:DescribeLaunchConfigurations",
                "ec2:DescribeInstanceTypes"
            ],
            "Resource": "*"
        }
    ]
}
```

step-2: create service account
------------------------------
```
eksctl create iamserviceaccount \
  --cluster=New-AnimProd-Cluster \ 
  --namespace=kube-system \
  --name=cluster-autoscaler \
  --attach-policy-arn=arn:aws:iam::580294450387:policy/AmazonEKSClusterAutoscaler \
  --override-existing-serviceaccounts \
  --approve
```

```

  eksctl utils associate-iam-oidc-provider --cluster New-AnimProd-Cluster --region us-west-2 --approve
```
```
  kubectl get sa -n kube-system | grep cluster
```

  step-3
  ------

create role
----------

  AmazonEKSClusterAutoscalerRole


  edit trust policy add below line

  "oidc.eks.us-west-2.amazonaws.com/id/8F2AF9EB1A6FC26109CB2CC5493CE526:sub": "system:serviceaccount:kube-system:cluster-autoscaler"

```
  {
	"Version": "2012-10-17",
	"Statement": [
		{
			"Effect": "Allow",
			"Principal": {
				"Federated": "arn:aws:iam::580294450387:oidc-provider/oidc.eks.us-west-2.amazonaws.com/id/8F2AF9EB1A6FC26109CB2CC5493CE526"
			},
			"Action": "sts:AssumeRoleWithWebIdentity",
			"Condition": {
				"StringEquals": {
					"oidc.eks.us-west-2.amazonaws.com/id/8F2AF9EB1A6FC26109CB2CC5493CE526:aud": "sts.amazonaws.com",
                    "oidc.eks.us-west-2.amazonaws.com/id/8F2AF9EB1A6FC26109CB2CC5493CE526:sub": "system:serviceaccount:kube-system:cluster-autoscaler"
				}
			}
		}
	]
}
```
step-4
------

To deploy the Cluster Autoscaler

    Download the Cluster Autoscaler YAML file.

```
curl -O https://raw.githubusercontent.com/kubernetes/autoscaler/master/cluster-autoscaler/cloudprovider/aws/examples/cluster-autoscaler-autodiscover.yaml
```

Modify the YAML file and replace with your cluster name. Also consider replacing the cpu and memory values as determined by your environment.


edit cluster-autoscaler-autodiscover.yaml  add cluster name
```
kubectl apply -f cluster-autoscaler-autodiscover.yaml
```


```
kubectl annotate serviceaccount cluster-autoscaler \
  -n kube-system \
  eks.amazonaws.com/role-arn=arn:aws:iam::580294450387:role/AmazonEKSClusterAutoscalerRole
```


  
