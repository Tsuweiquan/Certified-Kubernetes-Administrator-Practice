Task -

Create a new nginx Ingress resource as follows:

✑ Name: pong

✑ Namespace: ing-internal

✑ Exposing service hello on path /hello using service port 5678

![](https://img.itexams.com/assets/media/exam-media/04318/0004500005.jpg)

https://kubernetes.io/docs/concepts/services-networking/ingress/#the-ingress-resource

```yaml
apiVersion: networking.k8s.io/v1
kind: Ingress
metadata:
  name: pong
  namespace: ing-internal
spec:
  ingressClassName: nginx-example
  rules:
  - http:
      paths:
      - path: /hello
        pathType: Prefix
        backend:
          service:
            name: hello
            port:
              number: 5678

```