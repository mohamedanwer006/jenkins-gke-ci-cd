### TODO use ingress instead of loadbalancer service


### TODO fix volume as get error while creating pod 
```
└─ mohamed@DevOps:$ kubectl logs  jenkins-54846f76f7-cc5fl  -n jenkins-ns
touch: cannot touch '/var/jenkins_home/copy_reference_file.log': Read-only file system
Can not write to /var/jenkins_home/copy_reference_file.log. Wrong volume permissions?
```

> This happen when use Custom StorageClass and pv 
> I think this issue is because machine resources is not enough to create the volume  

#### To get around this, you can use a volume claim. with standard storage class

```yaml
---
apiVersion: v1
kind: PersistentVolumeClaim
metadata:
  name: jenkins-pvc
  namespace: jenkins-ns
spec:
  accessModes:
    - ReadWriteOnce
  resources:
    requests:
      storage: 3Gi
```

> This will create pv from standard (default )storage class