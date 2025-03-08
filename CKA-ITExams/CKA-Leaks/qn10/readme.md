![](https://img.itexams.com/assets/media/exam-media/04318/0002200001.jpg)

Task -

Schedule a Pod as follows:

✑ Name: kucc8

✑ App Containers: 2

✑ Container Name/Images:

- nginx
- consul

```bash
kubectl run kucc8 --image=nginx --dry-run=client -o yaml > qn10.yaml

vim qn10.yaml

apiVersion: v1
kind: Pod
metadata:
  creationTimestamp: null
  labels:
    run: kucc8
  name: kucc8
spec:
  containers:
  - image: nginx
    name: nginx
  - image: consul:1.15.4
    name: consul
    resources: {}
  dnsPolicy: ClusterFirst
  restartPolicy: Always
status: {}

kubectl describe pod kucc8
kubectl get pods

```