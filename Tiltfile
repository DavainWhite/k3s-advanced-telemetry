allow_k8s_contexts('rke2-development-16gib-8vcpu-80gib')

# k8s_resource(
#   new_name='grafana-dashboard-configmaps',
#   objects=[
#     'grafana-dashboard-alertmanager-overview:configmap',
#     'grafana-dashboard-apiserver:configmap',
#     'grafana-dashboard-cluster-total:configmap',
#     'grafana-dashboard-cnp:configmap',
#     'grafana-dashboard-controller-manager:configmap',
#     'grafana-dashboard-erlang-distribution:configmap',
#     'grafana-dashboard-erlang-distributions-compare:configmap',
#     'grafana-dashboard-erlang-memory-allocators:configmap',
#     'grafana-dashboard-grafana-overview:configmap',
#     'grafana-dashboard-k8s-resources-cluster:configmap',
#     'grafana-dashboard-k8s-resources-namespace:configmap',
#     'grafana-dashboard-k8s-resources-node:configmap',
#     'grafana-dashboard-k8s-resources-pod:configmap',
#     'grafana-dashboard-k8s-resources-workload:configmap',
#     'grafana-dashboard-k8s-resources-workloads-namespace:configmap',
#     'grafana-dashboard-kubelet:configmap',
#     'grafana-dashboard-kubernetes-nginx-ingress-via-prometheus:configmap',
#     'grafana-dashboard-namespace-by-pod:configmap',
#     'grafana-dashboard-namespace-by-workload:configmap',
#     'grafana-dashboard-node-cluster-rsrc-use:configmap',
#     'grafana-dashboard-node-rsrc-use:configmap',
#     'grafana-dashboard-nodes:configmap',
#     'grafana-dashboard-nodes-darwin:configmap',
#     'grafana-dashboard-persistentvolumesusage:configmap',
#     'grafana-dashboard-pod-total:configmap',
#     'grafana-dashboard-prometheus:configmap',
#     'grafana-dashboard-prometheus-remote-write:configmap',
#     'grafana-dashboard-proxy:configmap',
#     'grafana-dashboard-rabbitmq-alerts-grafana-dashboard:configmap',
#     'grafana-dashboard-rabbitmq-overview:configmap',
#     'grafana-dashboard-rabbitmq-queue-grafana-dashboard:configmap',
#     'grafana-dashboard-rabbitmq-quorum-queues-raft:configmap',
#     'grafana-dashboard-rabbitmq-stream:configmap',
#     'grafana-dashboard-scheduler:configmap',
#     'grafana-dashboard-workload-total:configmap'
#   ]
# )

k8s_resource(
  workload='grafana',
  labels=['monitoring'],
  port_forwards=[port_forward(3000, 3000, name='dashboard')]
)

k8s_resource(
  new_name='prometheus',
  workload='prometheus-server',
  labels=['monitoring'],
  port_forwards=[port_forward(9090, 9090, name='dashboard')]
)

# http://prometheus-server.prometheus.svc.cluster.local:9090

# k8s_resource(
#   workload='kube-prometheus-stack-grafana-test',
#   resource_deps=['grafana']
# )

# k8s_resource(
#   new_name='alertmanager-secrets',
#   objects=['alertmanager-kube-prometheus-stack-alertmanager:secret']
# )

# k8s_resource(
#   new_name='alertmanager',
#   objects=[
#     'kube-prometheus-stack-alertmanager:alertmanager',
#     'kube-prometheus-stack-alertmanager:serviceaccount',
#     'kube-prometheus-stack-alertmanager:service:kube-prometheus-stack'
#   ],
#   extra_pod_selectors=[{
#     'alertmanager': 'kube-prometheus-stack-alertmanager',
#     'app.kubernetes.io/instance': 'kube-prometheus-stack-alertmanager',
#     'app.kubernetes.io/managed-by': 'prometheus-operator',
#     'app.kubernetes.io/name': 'alertmanager',
#     'app.kubernetes.io/version': '0.25.0'
#   }],
#   labels=['monitoring'],
#   port_forwards=[port_forward(9093, 9093, name='dashboard')]
# )

# k8s_resource(
#   new_name='prometheus',
#   objects=[
#     'kube-prometheus-stack-prometheus:prometheus',
#     'kube-prometheus-stack-prometheus:serviceaccount',
#     'kube-prometheus-stack-prometheus:clusterrole',
#     'kube-prometheus-stack-prometheus:clusterrolebinding',
#     'kube-prometheus-stack-prometheus:service:kube-prometheus-stack'
#   ],
#   extra_pod_selectors=[{
#     'app.kubernetes.io/instance': 'kube-prometheus-stack-prometheus',
#     'app.kubernetes.io/managed-by': 'prometheus-operator',
#     'app.kubernetes.io/name': 'prometheus',
#     'app.kubernetes.io/version': '2.40.5',
#     'operator.prometheus.io/name': 'kube-prometheus-stack-prometheus',
#     'prometheus': 'kube-prometheus-stack-prometheus'
#   }],
#   labels=['monitoring'],
#   port_forwards=[port_forward(9090, 9090, name='dashboard')]
# )

# k8s_resource(
#   new_name='cnpg-settings',
#   objects=[
#     'cnpg-app-user:secret',
#     'cnpg-super-user:secret',
#     'cnpg-init-scripts:configmap'
#   ]
# )

# k8s_resource(
#   auto_init=False,
#   trigger_mode=TRIGGER_MODE_MANUAL,
#   new_name='cnpg-cluster'
#   objects=['cnpg-cluster:Cluster:cnpg-system'],
#   labels=['clusters'],
#   port_forwards=[port_forward(5432, 5432, name='connection')],
#   resource_deps=['cnpg-settings'],
# )

# k8s_resource(
#   auto_init=False,
#   trigger_mode=TRIGGER_MODE_MANUAL,
#   new_name='rabbitmq-cluster',
#   objects=['rabbitmq-cluster:rabbitmqcluster'],
#   extra_pod_selectors=[{
#     'app.kubernetes.io/component': 'rabbitmq',
#     'app.kubernetes.io/name': 'rabbitmq-cluster',
#     'app.kubernetes.io/part-of': 'rabbitmq',
#     'statefulset.kubernetes.io/pod-name': 'rabbitmq-cluster-server-0'
#   }],
#   labels=['clusters'],
#   resource_deps=[
#     'rabbitmq-cluster-operator',
#     'rabbitmq-cluster-operator-rabbitmq-messaging-topology-operator'
#   ]
# )

k8s_yaml(kustomize('.', flags = ['--enable-helm']))

# # kubectl --namespace cnpg-system port-forward svc/cnpg-cluster-rw 5432
# # kubectl --namespace rabbitmq-system port-forward svc/cluster-with-metrics 15672