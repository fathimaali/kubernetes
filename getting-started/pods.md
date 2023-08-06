# Pods. 

lifecycle 

* pending - one or more containers images not created yet 
* running - one or more containers running 
* suceeded - all containers suceeded, ran 
* failed - container terminated, at least one failed with error

commands 

* rendering pod details
---
    > kubectl describe example-pod
    > kubectl describe example-pod | grep Image
    > kubectl describe example-pod -o yaml 
    > kubectl describe example-pod -o wide
    > kubectl describe example-pod -o yaml > example-pod.yaml 
---

* accessing logs of a pod 
--- 
    > kubectl logs example-pod
---

* executing command in a cotainer 
---
    > kubectl exec -it example-pod -- /bin/sh
    # here -i is stdin, -t is stdin tty (terminal)
    
    > kubectl exec exmaple-pod --env
    # gets the env variables, notice we removed the interactive -i and -t 
---

* deleting a pod 
--- 
    > kubectl delete pod example-pod 
    > kubectl delete -f example-pod.yaml
---
either of these work 

* configuring pods
    * environment variables 
        --- 
            
        ---
