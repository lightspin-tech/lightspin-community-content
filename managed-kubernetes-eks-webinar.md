# Managed Kubernetes Webinar

## Links

#### EKS Creation Engine (ECE)
[ECE Github](https://github.com/lightspin-tech/eks-creation-engine)  
[Why create an EKS Creation tool](https://blog.lightspin.io/why-create-an-eks-creation-tool)  
[Microsoft Defender for endpoint on AWS](https://blog.lightspin.io/microsoft-defender-for-endpoint-on-aws-part-3)  

#### Kubernetes Network Security Policy
[Installing the Calico add-on on EKS](https://docs.aws.amazon.com/eks/latest/userguide/calico.html)  

#### EKS Control Plane Logging
[Enabling and disabling control plane logs](https://docs.aws.amazon.com/eks/latest/userguide/control-plane-logs.html#enabling-control-plane-log-export)  
[EKS authenticator - control access to the cluster](https://aws.github.io/aws-eks-best-practices/security/docs/iam/#controlling-access-to-eks-clusters)  

#### EKS Envelop Encryption
[Using EKS encryption provider support for defense-in-depth](https://aws.amazon.com/blogs/containers/using-eks-encryption-provider-support-for-defense-in-depth/)

#### EKS Cluster Endpoint
[De-mystifying cluster networking for Amazon EKS worker nodes](https://aws.amazon.com/blogs/containers/de-mystifying-cluster-networking-for-amazon-eks-worker-nodes/)  
[Review and revoke unnecessary anonymous access](https://aws.github.io/aws-eks-best-practices/security/docs/iam/#review-and-revoke-unnecessary-anonymous-access)  

#### IAM Roles for Service Accounts (IRSA)
[Introducing fine-grained IAM roles for service accounts](https://aws.amazon.com/blogs/opensource/introducing-fine-grained-iam-roles-service-accounts/)  
[Restrict access to the instance profile assigned to the worker node](https://aws.github.io/aws-eks-best-practices/security/docs/iam/#restrict-access-to-the-instance-profile-assigned-to-the-worker-node)  


## Commands

Check cluster logging status:
```
aws eks describe-cluster --name <cluster-name> | jq '.cluster.logging'
```

Check cluster public endpoint:
```
aws eks describe-cluster --name <cluster-name> | jq '.cluster.resourcesVpcConfig.endpointPublicAccess'
```

Check cluster private endpoint:
```
aws eks describe-cluster --name <cluster-name> | jq '.cluster.resourcesVpcConfig.endpointPrivateAccess'
```

Check which CIDRs can access the public cluster endpoint (if enabled):
```
aws eks describe-cluster --name <cluster-name> | jq '.cluster.resourcesVpcConfig.publicAccessCidrs'    
```

Check cluster encryption (null = disabled):
```
aws eks describe-cluster --name <cluster-name> | jq '.cluster.encryptionConfig'
```

Check EC2 node metadata options:
```
aws ec2 describe-instances --instance-ids <instance-id> | jq '.Reservations[].Instances[].MetadataOptions'
```
