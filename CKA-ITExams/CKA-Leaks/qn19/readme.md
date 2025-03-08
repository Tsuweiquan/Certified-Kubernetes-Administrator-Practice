Create a new NetworkPolicy named allow-port-from-namespace in the existing namespace echo.

Ensure that the new NetworkPolicy allows Pods in namespace internal to connect to port 9200/tcp of Pods in namespace echo.

Further ensure that the new NetworkPolicy:

- does not allow access to Pods, which don't listen on port 9200/tcp
- does not allow access from Pods, which are not in namespace internal

```yaml
apiVersion: networking.k8s.io/v1
kind: NetworkPolicy
metadata:
  name: allow-port-from-namespace
  namespace: echo
spec:
	podSelector: {}
  policyTypes:
  - Ingress
  ingress:
    - from:
	    - namespaceSelector:
	        matchLabels:
	          namespace: internal # make sure internal namespace has this label
	    ports:
	    - protocol: TCP
	      port: 9200

```