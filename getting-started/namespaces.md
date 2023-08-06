
### namespaces

namespaces are an API construct to avoid naming collisions and represent a scope for object names.

* notes
\
    why do we need namespaces? a few usecases

        - organization of resources logically 
        - many teams, same app 
        - many environments, dev, prod - same cluster, resource sharing between namespaces 
        - blue/green deployment 
            * 2 versions of prod can run at the same time and share resources 
            * blue - current prod 
            * green - next prod 
        - access control - limiting access to resources based on namespaces
        - resource usage quota - limiting resource utilization for a namespace, so one namespace does not use too much
\
    characteristics for a namespace: 

            1 needs to have a configmap of its own
            2 needs to have a secret of its own
            3 can share services from other namespaces
            4 a few components that cannot be created in a namespace
                    they live globally in the cluster
                    cannot isolate or bind them to a namespace

get list of namespaces

   > kubectl get namespace
                        
    - **default** - 
    - **kube-node-lease** - heartbeat of nodes 
    - **kube-public** - data available without authentication, public info, a configmap that contains cluster information 
    - **kube-system** - system processes, master, scheduler, etcetra 

## C

creating namespace

    > kubectl create namespace ckad
    > kubectl get namespace ckad

the yaml would look like 
    apiVersion: v1
    kind: Namespace
    metadata:
        name: ckad

can create declaratively 
    > kubectl apply -f ckad.yaml

using the namespace 
    kubectl get pods -n ckad
gets pods under namespace ckad, but we can set a default namespace using kubectx + kubens too

## D

deleting namespace

    > kubectl delete namespace ckad

## declaratively creating k8s objects in a namespace: 

example pod ngnix 

    apiVersion: v1
    kind: Pod
    metadata:
    creationTimestamp: null
    labels:
        run: nginx
    name: nginx
    namespace: ckad

to get global components that aren't bound to a namespace, but live globally in the cluster.

    kubectl api-resources --namespaced=false



**if we dont wanna type in the namespace everytime, i.e. change the default working namespace:**

`winget install kubectx` to install kubectx

to install kubectxwin -> follow steps on <https://github.com/thomasliddledba/kubectxwin>

and then install kubenswin -> <https://github.com/thomasliddledba/kubenswin>

`\.kubenswin` gives me the name of the namespace that is default

`.\kubenswin ls` lists all the namespaces in the cluster

`.\kubenswin set <name>` switch to another namespace

`.\kubenswin help` more help