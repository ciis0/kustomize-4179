= Expected Result =

```yaml
apiVersion: apps.openshift.io/v1
kind: DeploymentConfig
metadata:
  name: my-dc
spec:
  template:
    spec:
      containers:
      - env:
        - name: foo
          value: bar
        name: container
        volumeMounts:
        - mountPath: /mnt
          name: additional-cm
        - mountPath: /opt/cm
          name: cm
      initContainers:
      - name: init
      volumes:
      - configMap:
          name: additional-cm
        name: additional-cm
      - configMap:
          name: cm
        name: cm
```
