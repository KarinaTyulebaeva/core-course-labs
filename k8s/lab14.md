 Lab 14

## Stack description:
#### Prometheus

Service for retrieving and providing metrics

#### HAlertmanager

Redirects and configures all alerts from prometheus server

#### Node Exporter

Collects and exports metrics for hardware and OS

#### Prometheus operator

Kubernetes operator which simplifies the deployment and management of prometheus

#### kube-state-metrics

Collects metrics about objects in prometheus cluster and adapts them for prometheus

#### Grafana

A service for visualizing metrics provided by prometheus

## Output from commands
```
$ kubectl get po,sts,svc,pvc,cm
NAME                                                         READY   STATUS    RESTARTS      AGE
pod/alertmanager-prometheus-kube-prometheus-alertmanager-0   2/2     Running   0             51m
pod/app-python-0                                             2/2     Running   0             4m8s
pod/app-python-1                                             2/2     Running   0             4m8s
pod/app-python-2                                             2/2     Running   0             4m8s
pod/prometheus-grafana-6cc7d6f67f-zsxc5                      3/3     Running   0             51m
pod/prometheus-kube-prometheus-operator-58c49d56f4-b8vfp     1/1     Running   0             51m
pod/prometheus-kube-state-metrics-6bbff75769-kbg64           1/1     Running   0             51m
pod/prometheus-prometheus-kube-prometheus-prometheus-0       2/2     Running   0             51m
pod/prometheus-prometheus-node-exporter-887tg                1/1     Running   0             51m
pod/vault-0                                                  1/1     Running   6 (67m ago)   22d
pod/vault-agent-injector-5cd8b87c6c-rctsv                    1/1     Running   6 (67m ago)   22d
NAME                                                                    READY   AGE
statefulset.apps/alertmanager-prometheus-kube-prometheus-alertmanager   1/1     51m
statefulset.apps/app-python                                             3/3     4m9s
statefulset.apps/prometheus-prometheus-kube-prometheus-prometheus       1/1     51m
statefulset.apps/vault                                                  1/1     22d
NAME                                              TYPE        CLUSTER-IP       EXTERNAL-IP   PORT(S)                      AGE
service/alertmanager-operated                     ClusterIP   None             <none>        9093/TCP,9094/TCP,9094/UDP   51m
service/app-python                                NodePort    10.111.59.180    <none>        80:31071/TCP                 4m10s
service/kubernetes                                ClusterIP   10.96.0.1        <none>        443/TCP                      36d
service/prometheus-grafana                        ClusterIP   10.99.131.136    <none>        80/TCP                       51m
service/prometheus-kube-prometheus-alertmanager   ClusterIP   10.105.89.179    <none>        9093/TCP,8080/TCP            51m
service/prometheus-kube-prometheus-operator       ClusterIP   10.102.33.144    <none>        443/TCP                      51m
service/prometheus-kube-prometheus-prometheus     ClusterIP   10.100.193.87    <none>        9090/TCP,8080/TCP            51m
service/prometheus-kube-state-metrics             ClusterIP   10.100.110.237   <none>        8080/TCP                     51m
service/prometheus-operated                       ClusterIP   None             <none>        9090/TCP                     51m
service/prometheus-prometheus-node-exporter       ClusterIP   10.105.71.147    <none>        9100/TCP                     51m
service/vault                                     ClusterIP   10.109.25.80     <none>        8200/TCP,8201/TCP            22d
service/vault-agent-injector-svc                  ClusterIP   10.103.112.208   <none>        443/TCP                      22d
service/vault-internal                            ClusterIP   None             <none>        8200/TCP,8201/TCP            22d
NAME                                                 STATUS   VOLUME                                     CAPACITY   ACCESS MODES   STORAGECLASS   AGE
persistentvolumeclaim/app-data-app-python-0          Bound    pvc-e186228b-bf08-46b8-ae61-68c478f40cbc   62Mi       RWO            standard       8d
persistentvolumeclaim/app-data-app-python-1          Bound    pvc-5a63812d-c754-481f-be4c-823559acbfd4   62Mi       RWO            standard       8d
persistentvolumeclaim/app-data-app-python-2          Bound    pvc-a54ec4b3-fbe3-41b2-be3d-d66dd7394e40   62Mi       RWO            standard       8d
persistentvolumeclaim/app-data-kotlin-app-kotlin-0   Bound    pvc-771bc73c-8785-4046-ab30-e706470e3248   62Mi       RWO            standard       8d
persistentvolumeclaim/app-data-kotlin-app-kotlin-1   Bound    pvc-ef92e74b-b6b2-4f76-91fb-63f5c7be580e   62Mi       RWO            standard       8d
persistentvolumeclaim/app-data-kotlin-app-kotlin-2   Bound    pvc-a96bf888-7954-44b1-bcce-87c8fd578775   62Mi       RWO            standard       8d
NAME                                                                     DATA   AGE
configmap/app-python-config-map                                          1      4m10s
configmap/kube-root-ca.crt                                               1      36d
configmap/prometheus-grafana                                             1      51m
configmap/prometheus-grafana-config-dashboards                           1      51m
configmap/prometheus-kube-prometheus-alertmanager-overview               1      51m
configmap/prometheus-kube-prometheus-apiserver                           1      51m
configmap/prometheus-kube-prometheus-cluster-total                       1      51m
configmap/prometheus-kube-prometheus-controller-manager                  1      51m
configmap/prometheus-kube-prometheus-etcd                                1      51m
configmap/prometheus-kube-prometheus-grafana-datasource                  1      51m
configmap/prometheus-kube-prometheus-grafana-overview                    1      51m
configmap/prometheus-kube-prometheus-k8s-coredns                         1      51m
configmap/prometheus-kube-prometheus-k8s-resources-cluster               1      51m
configmap/prometheus-kube-prometheus-k8s-resources-multicluster          1      51m
configmap/prometheus-kube-prometheus-k8s-resources-namespace             1      51m
configmap/prometheus-kube-prometheus-k8s-resources-node                  1      51m
configmap/prometheus-kube-prometheus-k8s-resources-pod                   1      51m
configmap/prometheus-kube-prometheus-k8s-resources-workload              1      51m
configmap/prometheus-kube-prometheus-k8s-resources-workloads-namespace   1      51m
configmap/prometheus-kube-prometheus-kubelet                             1      51m
configmap/prometheus-kube-prometheus-namespace-by-pod                    1      51m
configmap/prometheus-kube-prometheus-namespace-by-workload               1      51m
configmap/prometheus-kube-prometheus-node-cluster-rsrc-use               1      51m
configmap/prometheus-kube-prometheus-node-rsrc-use                       1      51m
configmap/prometheus-kube-prometheus-nodes                               1      51m
configmap/prometheus-kube-prometheus-nodes-darwin                        1      51m
configmap/prometheus-kube-prometheus-persistentvolumesusage              1      51m
configmap/prometheus-kube-prometheus-pod-total                           1      51m
configmap/prometheus-kube-prometheus-prometheus                          1      51m
configmap/prometheus-kube-prometheus-proxy                               1      51m
configmap/prometheus-kube-prometheus-scheduler                           1      51m
configmap/prometheus-kube-prometheus-workload-total                      1      51m
configmap/prometheus-prometheus-kube-prometheus-prometheus-rulefiles-0   34     51m
```

## Explanation:
#### Pods:
-  `pod/prometheus-grafana-6cc7d6f67f-zsxc5` - grafana pod
- `pod/prometheus-prometheus-node-exporter-887tg` - node exporter pod
-  `pod/alertmanager-prometheus-kube-prometheus-alertmanager-0` - alertmanager pod
- `pod/prometheus-kube-state-metrics-6bbff75769-kbg64` - kube state metrics pod
- `pod/prometheus-kube-prometheus-operator-58c49d56f4-b8vfp` - prometheus operator pod
- `pod/prometheus-prometheus-kube-prometheus-prometheus-0` - prometheus pod

#### Statefulset:
- `statefulset.apps/alertmanager-prometheus-kube-prometheus-alertmanager` - kube prometheus alert manager statefulset
- `statefulset.apps/app-python` - app-python stateful set

#### Services:
1. `service/app-python` - app-python service
2. `service/prometheus-grafana` - grafana service
3. `service/prometheus-kube-prometheus-alertmanager` - alertmanager service
4. `service/prometheus-kube-prometheus-operator` - prom operator service
5. `service/prometheus-kube-prometheus-prometheus` - prometheus service
6. `service/prometheus-kube-state-metrics` - state metrics service
7. `service/prometheus-operated` - prometheus operated service
8. `service/prometheus-prometheus-node-exporter` - node exporter service

Configmaps are used for internal work of prometheus stack

### Dashboards
 ![browser](screenshots/alerts.png)
 ![browser](screenshots/cpu-python.png)
 ![browser](screenshots/kubelet.png)
 ![browser](screenshots/memory-pyton.png)
 ![browser](screenshots/metrics.png)
 ![browser](screenshots/network.png)


## Init containers

Get ls from new volume folder:
```
$ kubectl exec app-python-0 -- ls ./init
Defaulted container "app-python" out of: app-python, vault-agent, install (init), queue-1 (init), queue-2 (init), queue-3 (init), vault-agent-init (init)
queue
test.html
```

```html
$ kubectl exec app-python-0 -- cat ./init/test.html
Defaulted container "app-python" out of: app-python, vault-agent, install (init), queue-1 (init), queue-2 (init), queue-3 (init), vault-agent-init (init)
<html><head></head><body><header>
<title>http://info.cern.ch</title>
</header>

<h1>http://info.cern.ch - home of the first website</h1>
<p>From here you can:</p>
<ul>
<li><a href="http://info.cern.ch/hypertext/WWW/TheProject.html">Browse the first website</a></li>
<li><a href="http://line-mode.cern.ch/www/hypertext/WWW/TheProject.html">Browse the first website using the line-mode browser simulator</a></li>
<li><a href="http://home.web.cern.ch/topics/birth-web">Learn about the birth of the web</a></li>
<li><a href="http://home.web.cern.ch/about">Learn about CERN, the physics laboratory where the web was born</a></li>
</ul>
</body></html>
```