Collection of handy things for use when running EKS in your labs for repro and what not
Includes:
   - bunch of simple manifsets to feed into eksctl 
   - links to useful tools 
   - some handy shell aliases for optimized short hand 

for the eksctl manifests, you just need to swap the values in the manifests for values that are specific to your account 
the files can be extended by reviewing the schema here: https://eksctl.io/usage/schema/

In this case, there's a total of 4 manifests:
   - Cluster Config / Node Group for a cluster deployed into an already existant VPC with subnets
   - Cluster Config / Node Group for a fully private cluster into a new VPC 

The private node group file assumes you'll be using the Ubuntu EKS AMI hosted here: https://cloud-images.ubuntu.com/docs/aws/eks/
That particular AMI has kubelet running as a snap, and on account of eksctl changes, in order to boot strap properly, you need to adhere to the overrides in the file. 
In this case the overrides ensure that there is no mismatch on the cgroup driver between docker and kubelet 


EKS EFS Fargate Demo:
Getting storage setup in a Fargate-only cluster is kind of confusing when relying on the docs (at least it was for me and the cx I was working with)
I wrapped up the only things you need on hand to setup a little demo in your fargate-only cluster.
The only thing you need to already have an EFS volume setup, ie:
    - security groups need to be configured so that the pods can hit the filesystem
    - mount points need to be specified in the right subnets
Once that's all good you just need to specify the file system ID in the section for kind: PersistentVolume  in the file.
it also contains a demo pod in the manifest that'll just write to the mount, you can get rid of this if you want and make use of the other stuff.

Aliases:
    - self explanatory, add the aliases to your shell rc, then, after adding `source` the file

 
