![](https://img.itexams.com/assets/media/exam-media/04318/0002900001.jpg)

Context -

An existing Pod needs to be integrated into the Kubernetes built-in logging architecture (e.g. kubectl logs). Adding a streaming sidecar container is a good and common way to accomplish this requirement.

Task -

Add a sidecar container named `sidecar`, using the `busybox` image, to the existing Pod `big-corp-app`. The new sidecar container has to run the following command:

![](https://img.itexams.com/assets/media/exam-media/04318/0002900002.jpg)

Use a Volume, mounted at /var/log, to make the log file big-corp-app.log available to the sidecar container.

![](https://img.itexams.com/assets/media/exam-media/04318/0003000001.jpg)

https://kubernetes.io/docs/concepts/cluster-administration/logging/#streaming-sidecar-container

```bash
kubectl get pod <big-app> -o yaml > big-app.yaml
```

```bash
apiVersion: v1
kind: Pod
metadata:
  name: counter
spec:
  containers:
  - name: count
    image: busybox:1.28
    args:
    - /bin/sh
    - -c
    - >
      i=0;
      while true;
      do
        echo "$i: $(date)" >> /var/log/1.log;
        echo "$(date) INFO $i" >> /var/log/2.log;
        i=$((i+1));
        sleep 1;
      done      
    volumeMounts:
    - name: varlog
      mountPath: /var/log
  - name: sidecar # add this block
    image: busybox:latest
    args: [/bin/sh, -c, 'tail -n+1 -F /var/log/big-corp-app.log']
    volumeMounts:
    - name: varlog
      mountPath: /var/log # add this block
  volumes:
  - name: varlog
    emptyDir: {}

```