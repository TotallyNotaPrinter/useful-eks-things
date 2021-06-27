EKS EFS Fargate Demo: 
Getting storage setup in a Fargate-only cluster is kind of confusing when relying on the docs (at least it was for me and a customer I was working with) 

I wrapped up the only things you need on hand to setup a little demo in your fargate-only cluster. 
The only thing you need to already have an EFS volume setup, ie: 

- security groups need to be configured so that the pods can hit the filesystem 
-  mount points need to be specified in the right subnets 

Once that's all good you just need to specify the file system ID in the section for kind: PersistentVolume in the file. 

It also contains a demo pod in the manifest that'll just write to the mount, you can get rid of this if you want and make use of the other stuff.
