### TODO use ingress instead of loadbalancer service


### TODO fix volume as get error while creating pod 
```
└─ mohamed@DevOps:$ kubectl logs  jenkins-54846f76f7-cc5fl  -n jenkins-ns
touch: cannot touch '/var/jenkins_home/copy_reference_file.log': Read-only file system
Can not write to /var/jenkins_home/copy_reference_file.log. Wrong volume permissions?
```

> This happen when use StorageClass and pv 