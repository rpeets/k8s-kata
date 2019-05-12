## Kubernetes Horizontal Pod Autoscaler Setup Example.

### Note:-
This configuration is using MetalLB for Loadbalancer and Metric Server to collect resource usage data.

### Step-1: Setup a Deployment.
``` bash
kubectl apply -f 01-who-red-deployment.yaml
```

### Step-2: Create a Service.
``` bash
kubectl apply -f 02-who-red-service.yaml
```

### Step-3 Create a Horizontal Pod Autoscaler
```shell
kubectl apply -f 03-hpa-who-red.yaml
```

### Step-4: Check Deployment Status.
``` bash
kubectl get all
```

By Default Deployment will create 4 pods in this case.
Once you add some load using siege (HTTP tester and benchmarking utility)
You will be able to see the number of pods are increading.

### Step-5: Generate some load.
``` bash
siege -q -c 250 -t 4m http://192.168.8.222
```

### Step-6: Testing with some regular load.
``` bash
siege -q -c 2 -t 4m http://192.168.8.222
```
