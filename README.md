# what is Eks
```
Amazon Elastic Kubernetes Service (Amazon EKS) is a managed Kubernetes service that makes it easy for you to run Kubernetes on AWS and on-premises. Kubernetes is an open-source system for automating deployment, scaling, and management of containerized applications
```

# why we need eks
```
With Amazon EKS, you can take advantage of all the performance, scale, reliability, and availability of AWS infrastructure, as well as integrations with AWS networking and security services, such as application load balancers (ALBs) for load distribution, AWS Identity and Access Management (IAM) integration with role-
```

[aws link](https://www.amazonaws.cn/en/eks/features/)


# eks intro

. Aws Manage High availablity of control plane behind the scenes it deploy multiple ec2 and multiple az

. Aws detects and replace unhealthy control plane instances

. Aws scale control plane

. Aws maintain Etcd

. Provide Automate version upgrade and patching

. Integrated aws Eco system 

# Self managed worknode group

. you maintain Ec2

. you maintain orchestrate version upgrade

. security patch 

. keep pods up

. can use cutom ami


# Fargate

. No Worker Ec2 whatever

. You define and deploy pod

. container + serverless

# kubernetes architecture

![image](https://user-images.githubusercontent.com/42309948/178093014-12654d76-d2af-4360-8919-82d7c9ece25a.png)


