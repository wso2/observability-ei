# Enterprise Integrator Observability
This repo contains Observability resources for Enterprise Integrator which includes Helm chart and set of Grafana dashboards. Observability solution is based on proven projects in Cloud Native Computing Foundation to be cloud native and future proof. Following are the technologies used in the current solution.
- Metrics - Prometheus
- Visualization - Grafana
- Logging - Fluent-Bit and Grafana Loki
- Tracing - Jaeger

More support for different technologies will be added in future based on customer and industry demands.

For the ease of use, deployment is offered in a component based approach. Basic deployment will offer metrics capabilities for the user by deploying Prometheus and Grafana deployment. Users can view and explore with available Prometheus metrics using this deployments. 

For users who need log processing and tracing capabilities can enable that using given parameters as explained below. Enabling log processing will install fluent-bit and Grafana Loki. Enabling Tracing will install Jaeger-Operator.

 Though we have given prominence to these particular technologies it is technically feasible to integrate with other parallel technologies such as filebeat, logstash, elasticsearch etc. Support for those will be added in an as needed basis.

## Installing the Chart
### Prerequisites
Clone the Helm repository at https://github.com/wso2/observability-ei
Navigate to the home directory of the cloned repo and use below commands.

### Install Basic Deployment

To install the basic chart with the release name `wso2-observability`:

```console
$ helm install wso2-observability . --render-subchart-notes
```

### Install Basic Deployment with Log Prosessing

To install the basic chart with log processing having the release name `wso2-observability`:

Open values.yaml and set `loki-stack.enable` property to true and use below command.
```console
$ helm install wso2-observability . --render-subchart-notes
```

### Install Basic Deployment with Tracing

To install the basic chart with tracing having the release name `wso2-observability`:

Open values.yaml and set `jaeger.enable` property to true and use below command.
```console
$ helm install wso2-observability . --render-subchart-notes
```
This will install Jaeger operator in your cluster. Once it is done follow [this](https://github.com/jaegertracing/helm-charts/tree/master/charts/jaeger-operator#after-the-helm-installation) documentation to deploy your preferred Jaeger deployment using the installed operator.
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
| `jaeger.enable`         | Enable/Disable Jaeger deployment                            | `false`   |

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


