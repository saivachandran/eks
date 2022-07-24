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



# ways to spinup cluster

. Aws console

. Cloudformation

. Aws cli

. ekctl cli

best way ekctl cli


# what is ekctl

```
eksctl is a simple CLI tool for creating and managing clusters on EKS - Amazon's managed Kubernetes service for EC2. It is written in Go, uses CloudFormation, was created by Weaveworks and it welcomes contributions from the community
```

. cli tool creating eks cluster

. Easierhan cli

. Abstract lot of stuff vpc,sec

. Using cloud formation 


# Ekctl feature

. create get list, delete clusters

. create drain, delete nodegroup

. scale nodegroup

. update a cluster

. use custom AMI's

. configure vpc networking

. Configure Access to API Endpoints

. support for GPU nodegroups

. spot instances and mixed instances

. IAM Management and Addonpolicies

. List cluster cloduformation stacks

. install coredns 

. Write kubeconfig file for cluster



# what kubectl
```
The Kubernetes command-line tool, kubectl, allows you to run commands against Kubernetes clusters. You can use kubectl to deploy applications, inspect and manage cluster resources, and view logs. For more information including a complete list of kubectl operations, see the kubectl reference documentation
```

# Eks managed node group

```


Amazon EKS managed node groups create and manage Amazon EC2 instances for you.

Every managed node is provisioned as part of an Amazon EC2 Auto Scaling group that's managed for you by Amazon EKS. Moreover, every resource including Amazon EC2 instances and Auto Scaling groups run within your AWS account.

The Auto Scaling group of a managed node group spans every subnet that you specify when you create the group.

Amazon EKS tags managed node group resources so that they are configured to use the Kubernetes Cluster Autoscaler.



You can use a custom launch template for a greater level of flexibility and customization when deploying managed nodes. If you deploy using a launch template, you can also use a custom AMI. For more information, see Launch template support. If you don't use a custom launch template when first creating a managed node group, there is an auto-generated launch template. Don't manually modify this auto-generated template or errors occur.

Amazon EKS follows the shared responsibility model for CVEs and security patches on managed node groups. When managed nodes run an Amazon EKS optimized AMI, Amazon EKS is responsible for building patched versions of the AMI when bugs or issues are reported. We can publish a fix. However, you're responsible for deploying these patched AMI versions to your managed node groups. When managed nodes run a custom AMI, you're responsible for building patched versions of the AMI when bugs or issues are reported and then deploying the AMI. For more information, see Updating a managed node group.

Amazon EKS managed node groups can be launched in both public and private subnets. If you launch a managed node group in a public subnet on or after April 22, 2020, the subnet must have MapPublicIpOnLaunch set to true for the instances to successfully join a cluster. If the public subnet was created using eksctl or the Amazon EKS vended AWS CloudFormation templates on or after March 26, 2020, then this setting is already set to true. If the public subnets were created before March 26, 2020, you must change the setting manually. For more information, see Modifying the public IPv4 addressing attribute for your subnet.

```
