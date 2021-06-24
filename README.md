# eksctl-manifests
bunch of simple manifsets to feed into eksctl 

just need to swap the values in the manifests for values that are specific to your account 
can extend by reviewing the schema here: https://eksctl.io/usage/schema/

In this case, there's a total of 4 manifests:
   - Cluster Config / Node Group for a cluster deployed into an already existant VPC with subnets
   - Cluster Config / Node Group for a fully private cluster into a new VPC 

The private node group file assumes you'll be using the Ubuntu EKS AMI hosted here: https://cloud-images.ubuntu.com/docs/aws/eks/
That particular AMI has kubelet running as a snap, and on account of eksctl changes, in order to boot strap properly, you need to adhere to the overrides in the file. 
In this case the overrides ensure that there is no mismatch on the cgroup driver between docker and kubelet 

