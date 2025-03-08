Task -

A Kubernetes worker node, named wk8s-node-0 is in state NotReady.

Investigate why this is the case, and perform any appropriate steps to bring the node to a Ready state, ensuring that any changes are made permanent.

![](https://img.itexams.com/assets/media/exam-media/04318/0003500001.jpg)

```bash
kubectl get nodes
kubectl describe node wk8s-node-0

ssh wk8s-node-0
systemctl status kubelet
systemctl start kubelet
systemctl enable kubelet

journalctl -fu kubelet

exit ssh
kubectl get nodes
```