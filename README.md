# Certified-Kubernetes-Administrator-Practice
Certified Kubernetes Administrator Practice

These are some questions that i used to practice for my CKA certification.

Feel free to test your knowledge with the questions.

# Important CLIs

List your clusters

```
kubectl config get-contexts
CURRENT   NAME       CLUSTER    AUTHINFO   NAMESPACE
*         minikube   minikube   minikube   practice
```

Select your clusters
```
kubectl config use-context minikube
Switched to context "minikube".
```

Select namespace
```
kubectl config set-context --current --namespace=practice
```