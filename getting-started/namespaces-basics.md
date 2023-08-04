
### namespaces

`kubectl get namespace`

`kubectl create namespace my-first-namespace`

`kubectl apply -f my-second-namespace.yaml`

`kubectl api-resources --namespaced=false` this is to get global components that aren't bound to a namespace, but live globally in the cluster.

creating a components inside a namespace
`kubectl apply -f mongo.yaml --namespace=my-first-namespace`

`kubectl get all --namespace=my-first-namespace`

and ofc can edit the yaml file, to specify which namespace to create in and then just do - great for automation

`kubectl apply -f mongo.yaml`

if we dont wanna type in the namespace everytime, i.e. change the default working namespace: 

`winget install kubectx` to install kubectx

to install kubectxwin -> follow steps on <https://github.com/thomasliddledba/kubectxwin>

and then install kubenswin -> <https://github.com/thomasliddledba/kubenswin>

`\.kubenswin` gives me the name of the namespace that is default

`.\kubenswin ls` lists all the namespaces in the cluster

`.\kubenswin set <name>` switch to another namespace

`.\kubenswin help` more help