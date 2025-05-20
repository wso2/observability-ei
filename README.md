# Enterprise Integrator Observability
This repo contains Observability solution for Enterprise Integrator. 

> **NOTICE:** The Cloud Native Observability Deployment is now deprecated and will no longer receive updates.

WSO2 Enterprise Integrator offers observability capabilities based on
1. [Classic Observability Deployment](classic/README.md) - which is analytics distribution that mainly provides 
business analytics functionality together with observability related 
features. Users with comprehensive observability requirements had to 
rely on external tools/stacks such as ELK, Prometheus, AppDynamics, Jaeger, 
Zipkin, etc. 

2. [Cloud Native Observability Deployment](cloud-native/README.md) - **[DEPRECATED]**
allows you to monitor and troubleshoot you WSO2 Enterprise Integrator system
 with ease. This solution is based on proven projects in Cloud Native Computing Foundation to be cloud native and future proof. Also, this technology stack allows you to view and correlate all three pillars of observability (i.e., metrics, logging, and tracing) from a single location instead of using several tools, thereby unifying the monitoring experience. The selected set of external tools are:
    - Metrics - Prometheus
    - Visualization - Grafana
    - Logging - Fluent-Bit and Grafana Loki
    - Tracing - Jaeger
