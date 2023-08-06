### handy tips for ckad

---
    alias k=kubectl 
---
saves times from having to type it everytime for command execution

---
    kubectl api-resources
---
to get a list of shortforms of long commands 

---
    k delete pod webapp-with-an-ingress --grace-period=0 --force
---
to delete objects fast without grace period to save time on exam

---
    kubectl describe pods | grep 10 -C "labels:"
---
to filter out quickly from a long description 

