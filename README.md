see https://github.com/kubernetes-sigs/kustomize/issues/4179

# Expected Result

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

# Issues:

|||
|-|-|
|`./demo-overlay.sh`|Patch from Component w/o OpenAPI does *not work*; how to provide a OpenAPI schema globally?|
|`./demo-overlay+openapi.sh`|Patch from Component w/  OpenAPI in overlay *does work*; really necessary to provide the same OpenAPI file accross overlays?|
|`./demo-overlay+component-openapi.sh`|Patch from Component w/  OpenAPI in component does *not work*; would have been an option to share OpenAPI between overlays.|
