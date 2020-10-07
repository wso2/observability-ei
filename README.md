# Enterprise Integrator Observability
This repo contains Observability solution for Enterprise Integrator. 

WSO2 Enterprise Integrator offers observability capabilities based on
1. [Classic Observability Deployment](classic/README.md) - which is analytics distribution that mainly provides 
business analytics functionality together with observability related 
features. Users with comprehensive observability requirements had to 
rely on external tools/stacks such as ELK, Prometheus, AppDynamics, Jaeger, 
Zipkin, etc. This resulted in multiple scattered systems to observe the 
system where debugging and troubleshooting were not sufficiently stream-lined.

2. [Cloud Native Observability Deployment](cloud-native/README.md) - that utilizes a selected set of external tools such as:
- Metrics - Prometheus
- Visualization - Grafana
- Logging - Fluent-Bit and Grafana Loki
- Tracing - Jaeger
