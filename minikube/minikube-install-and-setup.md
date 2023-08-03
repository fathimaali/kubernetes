
# Minikube install and setup.


- need to download minikube stable from : 
> <https://minikube.sigs.k8s.io/docs/start/>

- need to have docker driver for running minikube : so install that from : 
>    <https://minikube.sigs.k8s.io/docs/drivers/> and then
>    <https://docs.docker.com/engine/install/>

- once that is done, we can start the minikube cluster using 
---
    minikube start --driver docker
---

- check status 
---
    minikube status
---

- check nodes
---
    minikube get node
---

all looks ok here.