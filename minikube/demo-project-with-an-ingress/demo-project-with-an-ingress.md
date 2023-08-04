### install ingress controller in minikube 

---
    minikube addons enable ingress
---

verify this, which is running under kube-system namespace 

---
    kubectl get all -n ingress-nginx
---

### create the service that the ingress component wants to direct to

<https://github.com/fathimaali/kubernetes/blob/main/minikube/demo-project-with-an-ingress/webapp-with-an-ingress.yaml>

---
    kubectl apply -f webapp-with-an-ingress.yaml
    kubectl get service
    minikube service webapp-with-an-ingress --url -n my-first-namespace
---

our app deployment and the service are up and running 

### create an ingress component 

write the config : 

<https://github.com/fathimaali/kubernetes/blob/main/minikube/demo-project-with-an-ingress/ingress-webapp.yaml>

---
    kubectl apply -f ingres-webapp.yaml
    kubectl get ingress
---

need to map the local dns 

the docs all over the internet, talking about how you can fetch minikube IP and then map it to the ingress domain rule's hostname, and then it would work

in contrary, since I am using windows, and with docker driver for running my minikube, there is no way i can directly access minikube IP from my browser, i need to key in docker driver IP that i fetch with 

---
 minikube service webapp-with-an-ingress --url
---

fetch this IP address then access from browser.

So, going by this logic, in order for me to test conceptually if my ingress is working, i would need to port-forwarding. ONLY for testing. 

---
    kubectl port-forward service/ingress-nginx-controller -n ingress-nginx 80:80
---

on win powershell - run as admin 

---
    cd C:\Windows\System32\drivers\etc>
    code hosts
---

add NOT the minikube IP, instead add the docker driver IP

---
    # 127.0.0.1 kubernetes.docker.internal
    127.0.0.1 webapp.com
---