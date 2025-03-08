Schedule a pod as follows:

- Name: nginx-kusc00401
- Image: nginx
- Node selector: disk=spinning

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: nginx-kusc00401
spec:
  containers:
  - name: nginx-kusc00401
    image: nginx:latest
    ports:
    - containerPort: 80
  nodeSelector:
	  minikube.k8s.io/name: minikube
	  # disk: spinning

```