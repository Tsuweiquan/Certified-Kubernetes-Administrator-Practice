Create a persistent volume with name app-data, of capacity 2Gi and access mode ReadWriteOnce. The type of volume is hostPath and its location is /srv/app-data.

https://kubernetes.io/docs/tasks/configure-pod-container/configure-persistent-volume-storage/#create-a-persistentvolume

```yaml
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
    - ReadWriteOnce
  hostPath:
    path: "/srv/app-data"

```