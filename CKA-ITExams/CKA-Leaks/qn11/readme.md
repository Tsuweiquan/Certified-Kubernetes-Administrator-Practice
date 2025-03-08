![](https://img.itexams.com/assets/media/exam-media/04318/0002500001.jpg)

Task -

Create a persistent volume with name app-data, of capacity 2Gi and access mode ReadOnlyMany. The type of volume is hostPath and its location is /srv/app-data.

https://kubernetes.io/docs/tasks/configure-pod-container/configure-persistent-volume-storage/#create-a-persistentvolume

```bash
apiVersion: v1
kind: PersistentVolume
metadata:
  name: app-data
  labels:
    type: local
spec:
  storageClassName: manual
  capacity:
    storage: 2Gi
  accessModes:
    - ReadOnlyMany
  hostPath:
    path: "/srv/app-data"

```

```bash
kubectl apply -f persistent.yaml
kubectl get pv
```