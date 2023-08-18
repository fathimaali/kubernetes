### handy tips for ckad

```
    alias k=kubectl 
```
saves times from having to type it everytime for command execution

```
    kubectl api-resources
```
to get a list of shortforms of long commands 

```
    k delete pod webapp-with-an-ingress --grace-period=0 --force
```
to delete objects fast without grace period to save time on exam

```
    kubectl describe pods | grep 10 -C "labels:"
```
to filter out quickly from a long description 

```
    --dry-run:
```
By default, as soon as the command is run, the resource will be created. If you simply want to test your command, use the --dry-run=client option. This will not create the resource. Instead, tell you whether the resource can be created and if your command is right.

```
    -o yaml:
```
This will output the resource definition in YAML format on the screen.

Use the above two in combination along with Linux output redirection to generate a resource definition file quickly, that you can then modify and create resources as required, instead of creating the files from scratch.

```
    kubectl run nginx --image=nginx --dry-run=client -o yaml > nginx-pod.yaml
```