![](https://img.itexams.com/assets/media/exam-media/04318/0002700001.jpg)

Task -

Monitor the logs of pod foo and:

✑ Extract log lines corresponding to error file-not-found

✑ Write them to /opt/KUTR00101/foo

```bash
kubectl logs foo | grep "file-non-found" > /opt/KUTR00101/foo

cat /opt/KUTR00101/foo
```