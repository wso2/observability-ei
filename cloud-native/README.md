# Cloud Native Observability Deployment

This cloud native observability repository includes Helm charts and a set of Grafana dashboards. This observability solution is based on proven projects in Cloud Native Computing Foundation to be cloud native and future proof. Following are the technologies used in the current solution.
- Metrics - Prometheus
- Visualization - Grafana
- Logging - Fluent-Bit and Grafana Loki
- Tracing - Jaeger

More support for different technologies will be added in future based on customer and industry demands.

For the ease of use, deployment is offered in a component based approach. Basic deployment will offer metrics capabilities for the user by deploying Prometheus and Grafana deployment. Users can view and explore with available Prometheus metrics using this deployment. 

Users who need log processing and tracing capabilities can enable that using given parameters as explained below. Enabling log processing will install fluent-bit and Grafana Loki. Enabling Tracing will install Jaeger-Operator.

 Though we have given prominence to these particular technologies, it is technically feasible to integrate with other parallel technologies such as filebeat, logstash, elasticsearch etc. Support for those will be added on an as-needed basis.

## Installing the Chart
### Prerequisites
1. Kubernetes Cluster: Ensure you have an operational Kubernetes cluster (e.g. AKS, EKS, GKE, or a local Kubernetes cluster).
2. Helm: Install [Helm](https://helm.sh/docs/intro/install/) (version 3 or later) on your machine.
3. Ingress Controller: Deploy an ingress controller (e.g. [NGINX Ingress Controller](https://kubernetes.github.io/ingress-nginx/deploy/)).
4. Clone the Helm repository at https://github.com/wso2/observability-ei

### Install Basic Deployment

To install the basic chart with the release name `wso2-observability`:

```console
$ helm install wso2-observability . --render-subchart-notes
```

Once deployed, you can access the Grafana UI from https://monitoring.mi.wso2.com/grafana.

### Install Basic Deployment with Log Prosessing

To install the basic chart with log processing having the release name `wso2-observability`:

Open values.yaml and set `loki-stack.enable` property to true and use below command.
```console
$ helm install wso2-observability . --render-subchart-notes
```

### Install Basic Deployment with Tracing

To install the basic chart with tracing having the release name `wso2-observability`:

#### Install cert-manager
Make sure cert-manager CRDs are installed. Setting up cert-manager is a prerequisite for deploying the jaeger-operator helm chart.

1. Execute the below command to see if CRDs are already installed.
```
kubectl get crd -l app.kubernetes.io/instance=cert-manager
```
2. If no resources were found, install them with the below command.
```
kubectl apply -f https://github.com/cert-manager/cert-manager/releases/download/v1.6.3/cert-manager.crds.yaml
```

Execute the below commands to install cert-manager.

3. Add the Jetstack helm repository. 
```
helm repo add jetstack https://charts.jetstack.io
```
4. If you have the repository already added, update it.
```
helm repo update
```
5. run the below command to install cert-manager.
```
helm install cert-manager jetstack/cert-manager --namespace cert-manager --create-namespace --version v1.6.3
```

You can check which version of cert-manager is compatible with the jeager-operator version you'll be using from the compatibility matrix [here](https://github.com/jaegertracing/helm-charts/blob/v2/charts/jaeger-operator/COMPATIBILITY.md).

6. Open values.yaml and set `jaeger-operator.enable` property to true and use below command.
```console
$ helm install wso2-observability . --render-subchart-notes
```
This will install Jaeger operator in your cluster. 

`jaeger-operator.jaeger.create` is set to `true` by default in the values.yaml file. This will create an 'AllInOne' Jaeger instance.
If you are working in a poduction environment, you can create a Jaeger instance using a different strategy by providing the instance specification under `jaeger-operator.jaeger.spec` in the values.yaml file.   Follow [this](https://github.com/jaegertracing/helm-charts/tree/master/charts/jaeger-operator#after-the-helm-installation) documentation to deploy your preferred Jaeger deployment.

Once deployed, you can access the Jaeger UI from  http://tracing.mi.wso2.com. You can change the host name by chanigng the `jaeger-oeprator.jaeger.spec.ingress.hosts` in values.yaml file.

## Uninstalling the Chart

To uninstall/delete the `wso2-observability` deployment:

```console
$ helm uninstall wso2-observability
```
## Configuration

The following table lists the configurable parameters of the jaeger-operator chart and their default values.

| Parameter               | Description                                                 | Default   |
| :---------------------- | :---------------------------------------------------------- | :-------- |
| `prometheus.enable`     | Enable/Disable Prometheus deployment                        | `true`    |
| `grafana.enable`        | Enable/Disable Grafana deployment                           | `true`    |
| `loki-stack.enable`     | Enable/Disable Loki and Fluent-bit deployment               | `false`   |
| `jaeger-operator.enable`         | Enable/Disable Jaeger deployment                            | `false`   |

Above are the parameters that are added through this cahrt. However there are four dependecy charts that are being used by this chart. users can also change parameters exposed by those charts as well. Below are the configs exposed by those charts.
- [Prometheus configs](https://github.com/helm/charts/tree/master/stable/prometheus#configuration)
- [Grafana configs](https://github.com/grafana/helm-charts/tree/main/charts/grafana#configuration)
- [Loki stack configs](https://github.com/grafana/loki/tree/master/production/helm/loki-stack#deploy-loki-and-promtail-to-your-cluster)
- [Jaeger operator configs](https://github.com/jaegertracing/helm-charts/tree/master/charts/jaeger-operator#configuration)

To override the parameters you can use any of the below methods.
- Change default values.yaml provided in the repo
- Create custom values.yaml and provide that as an argument when installing the chart.
- Set using `--set key=value[,key=value]` argument when installing the chart

Ex:
```console
$ helm install wso2-observability . --render-subchart-notes\
--set loki-stack.enable=true
```


