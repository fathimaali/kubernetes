### ingress basics 

**ingress controller component** - evaluates and processes all the rules, manage redirections

info at : https://kubernetes.io/docs/concepts/services-networking/ingress-controllers/

for baremetal k8s cluster : https://kubernetes.github.io/ingress-nginx/deploy/baremetal/ 

on minikube : 
```
        minikube addons enable ingress
```


**ingress component** :

the config looks like : 
```
    apiVersion: networking.k8s.io/v1
    kind: Ingress
    metadata:
    name: example-ingress
    annotations:
        nginx.ingress.kubernetes.io/rewrite-target: /$1
    spec:
    rules:
        - host: webapp.com
        http:
            paths:
            - path: /
                pathType: Prefix
                backend:
                service:
                    name: webapp-with-an-ingress-service
                    port:
                    number: 8080
```

in this case the webapp-internal-service is the service of the webapp, that is internal and looks like this 

```
    apiVersion: v1
    kind: Service
    metadata:
    name: webapp-with-an-ingress-service
    spec:
    type: NodePort
    selector:
        app: webapp
    ports:
        - protocol: TCP
        port: 8080
        targetPort: 8080
        nodePort: 30000
```

once these are deployed with 

```
    kubectl apply -f
```

we proceed to ensure /etc/hosts is updated to do the lookup properly.
external requests go from browser -> ingress controller -> rule evaluation based on ingress config -> service (webpp-with-an-ingress-service)

done.