# ONOS Cluster on Kubernetes

ONOS has changed its cluster infrastructure with 1.14 release and separated cluster storage and ONOS control functions.
From version 1.14, atomix is used to manage cluster storage and membership. So, you have to install atomix and Onos separately.

It is easy to install applications on Kubernetes with helm charts. Atomix and Onos projects have helm charts in different github repository. In this repo, i tried to combine them to make setup easier.

atomix helm chart is from [atomix/atomix-helm](https://github.com/atomix/atomix-helm)

onos-kubernetes chart is from [opennetworkinglab/onos-kubernetes](https://github.com/opennetworkinglab/onos-kubernetes)

#Installation

You need a dynamic storage volume for this setup. I'm using [nfs-client](https://github.com/kubernetes-incubator/external-storage)

After clone this repo:

`cd onos-kubernetes`

`helm dependency update`

`helm install onos-kubernetes --name onos --set heap=2G --set image.tag=1.15.0 --set atomix.image.tag=3.0.11 --set replicas=3 --set atomix.replicas=3 --set atomix.persistence.size=1Gi --set atomix.persistence.storageClass=managed-nfs-storage`






 
