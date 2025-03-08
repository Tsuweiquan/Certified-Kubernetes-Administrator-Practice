Task -

Create a new PersistentVolumeClaim:

✑ Name: pv-volume

✑ Class: csi-hostpath-sc

✑ Capacity: 10Mi

Create a new Pod which mounts the PersistentVolumeClaim as a volume:

✑ Name: web-server

✑ Image: nginx

✑ Mount path: /usr/share/nginx/html

Configure the new Pod to have ReadWriteOnce access on the volume.

Finally, using kubectl edit or kubectl patch expand the PersistentVolumeClaim to a capacity of 70Mi and record that change.

---

# Create PV

```yaml
apiVersion: v1
kind: PersistentVolume
metadata:
  name: pv-volume
  labels:
    type: local
spec:
  storageClassName: csi-hostpath-sc
  capacity:
    storage: 10Mi
  accessModes:
    - ReadWriteOnce
  hostPath:
    path: "/mnt/data"

```

# Create a PVC

https://kubernetes.io/docs/tasks/configure-pod-container/configure-persistent-volume-storage/#create-a-persistentvolumeclaim

```yaml
apiVersion: v1
kind: PersistentVolumeClaim
metadata:
  name: pv-volume
spec:
  storageClassName: csi-hostpath-sc
  accessModes:
    - ReadWriteOnce
  resources:
    requests:
      storage: 10Mi

```

# Edit the pod to mount the PVC

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: web-server
spec:
  volumes:
    - name: pv-volume
      persistentVolumeClaim:
        claimName: pv-volume
  containers:
    - name: pv-volume-pod
      image: nginx
      ports:
        - containerPort: 80
          name: "http-server"
      volumeMounts:
        - mountPath: "/usr/share/nginx/html"
          name: pv-volume

```

---

1. Edit the PV to 70Mi or larger
    1. kubectl edit pv pv-volume
2. Edit the PVC
    
    ```yaml
     20 spec:
     21   accessModes:
     22   - ReadWriteOnce
     23   resources:
     24     requests:
     25       storage: 10Mi -> 70Mi
     26   storageClassName: csi-hostpath-sc
    ```
    
3. Save the file

---

# If need to force unbound

```yaml
kubectl get pvc
kubectl edit pvc
# delete the finalizer block
kubectl delete pvc pv-volume

kubectl get pv
kubectl edit pv

# delete the claimRef block
# delete the status block
kubectl get pv

#Now edit the pvc yaml, increase the request
kubectl apply -f pvc.yaml 
```