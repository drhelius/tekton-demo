# tekton-demo

```
oc new-project tekton-demo
```

```
oc get serviceaccount pipeline
```

```
oc create -f tasks/hello.yaml
```

```
tkn task start --showlog hello
```

```
oc create -f tasks/apply_manifest_task.yaml
```

```
oc create -f tasks/update_deployment_task.yaml
```

```
tkn task ls
```

```
tkn clustertasks ls
```

https://hub.tekton.dev/

```
oc create -f pipeline/pipeline.yaml
```

```
oc create -f resources/persistent_volume_claim.yaml
```

```
tkn pipeline start build-and-deploy -w name=shared-workspace,claimName=source-pvc -p deployment-name=pipelines-vote-api -p git-url=https://github.com/openshift/pipelines-vote-api.git -p IMAGE=image-registry.openshift-image-registry.svc:5000/tekton-demo/vote-api --showlog

```

```
tkn pipeline start build-and-deploy -w name=shared-workspace,claimName=source-pvc -p deployment-name=pipelines-vote-ui -p git-url=https://github.com/openshift/pipelines-vote-ui.git -p IMAGE=image-registry.openshift-image-registry.svc:5000/tekton-demo/vote-ui --showlog

```

```
oc get route pipelines-vote-ui --template='http://{{.spec.host}}'
```