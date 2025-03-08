![](https://img.itexams.com/assets/media/exam-media/04318/0002100001.jpg)

Task -

Check to see how many nodes are ready (not including nodes tainted NoSchedule) and write the number to /opt/KUSC00402/kusc00402.txt.

```bash
kubectl describe nodes | grep Taint | grep -v NoSchedule | wc -l > /opt/KUSC00402/kusc00402.txt

# Double confirm by checking
kubectl get nodes -o wide

```