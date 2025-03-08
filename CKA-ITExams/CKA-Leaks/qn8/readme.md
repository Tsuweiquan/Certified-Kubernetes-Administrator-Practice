![](https://img.itexams.com/assets/media/exam-media/04318/0001900001.jpg)

Task -

Schedule a pod as follows:

✑ Name: nginx-kusc00401

✑ Image: nginx

✑ Node selector: disk=ssd

```bash
kubectl get nodes
kubectl describe nodes
# check which node has this label disk=ssd

# assuming if the deployment is there
kubectl get deployments
kubectl edit deployment <item>

# if we need to create a new pod
kubectl run nginx-kusc00401 --image=nginx --dry-run=client -o yaml
apiVersion: v1
kind: Pod
metadata:
  creationTimestamp: null
  labels:
    run: nginx-kusc00401
  name: nginx-kusc00401
spec:
  containers:
  - image: nginx
    name: nginx-kusc00401
    resources: {}
  nodeSelector: # we must use nodeSelector
	  disk: ssd
  dnsPolicy: ClusterFirst
  restartPolicy: Always
status: {}

kubectl apply -f <file>.yaml

kubectl get nodes -o wide
kubectl get pods -o wide

```