## Install wordpress and mysql on kube cluster with persistent volumes

#### Usage
1. git clone the repository

`git clone https://github.com/rthway/wordpress-k8s.git`

1. Run the below command to startup a cluster with wordpress and mysql

`kubectl apply -f ./`

1. Change password in the kustomization.yaml file

1. check using the below commands
`kubectl get all`
or
```
kubectl get pods
kubectl get services
kubectl get pvc
kubectl get secret
```


NAME                                   READY   STATUS    RESTARTS   AGE
pod/wordpress-7f7bf85b9c-qm6gf         1/1     Running   0          14m
pod/wordpress-mysql-7d5f9bb46c-d59nb   1/1     Running   0          14m

NAME                      TYPE           CLUSTER-IP       EXTERNAL-IP   PORT(S)        AGE
service/kubernetes        ClusterIP      10.96.0.1        <none>        443/TCP        24m
service/wordpress         LoadBalancer   10.111.255.151   <pending>     80:32191/TCP   14m
service/wordpress-mysql   ClusterIP      None             <none>        3306/TCP       14m

NAME                              READY   UP-TO-DATE   AVAILABLE   AGE
deployment.apps/wordpress         1/1     1            1           14m
deployment.apps/wordpress-mysql   1/1     1            1           14m

NAME                                         DESIRED   CURRENT   READY   AGE
replicaset.apps/wordpress-7f7bf85b9c         1         1         1       14m
replicaset.apps/wordpress-mysql-7d5f9bb46c   1         1         1       14m



1. To delete the cluster run `kubectl delete -f ./`
