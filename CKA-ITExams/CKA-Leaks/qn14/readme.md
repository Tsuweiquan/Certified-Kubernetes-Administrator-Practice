![](https://img.itexams.com/assets/media/exam-media/04318/0003300001.jpg)

Task -

From the pod label name=overloaded-cpu, find pods running high CPU workloads and write the name of the pod consuming most CPU to the file /opt/

KUTR00401/KUTR00401.txt (which already exists).

```bash
kubectl top pod POD_NAME --sort-by=cpu  

kubectl top pods --selector=name=overloaded-cpu--sort-by=cpu

kubectl top pods -l name=overloaded-cpu--sort-by=cpu--no-headers | awk '{print $1}' | head -1 > file.txt
```