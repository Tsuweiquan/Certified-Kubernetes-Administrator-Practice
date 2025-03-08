Schedule a Pod as follows:

- Name: kucc1
- App Containers: 2
- Container Name/images:

o redis

o consul

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: kucc1
spec:
  containers:
  - name: redis
    image: redis:latest
    ports:
    - containerPort: 80
  - name: consul
    image: consul:1.15
    ports:
    - containerPort: 80

```