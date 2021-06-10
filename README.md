# Prometheus StatsD Exporter



## Introduction

This chart bootstraps a prometheus [statsd exporter](https://github.com/prometheus/statsd_exporter) deployment on a [Kubernetes](http://kubernetes.io) cluster using the [Helm](https://helm.sh) package manager.



## Adding Our Chart Repository

To add the Hahow charts for your local client, run `helm repo add`:

```console
$ helm repo add hahow https://hahow-helm-charts.storage.googleapis.com/
```



## Installing the Chart

To install the chart with the release name `my-release`:

```console
$ helm install my-release hahow/prometheus-statsd-exporter
```

The command deploys statsd exporter on the Kubernetes cluster in the default configuration. The [configuration](#configuration) section lists the parameters that can be configured during installation.



## Uninstalling the Chart

To uninstall/delete the `my-release` deployment:

```console
$ helm delete my-release
```

The command removes all the Kubernetes components associated with the chart and deletes the release.



## Configuration

The following table lists the configurable parameters of the StatsD Exporter chart and their default values.

| Parameter | Description | Default |
| --------- | ----------- | ------- |
| `affinity` | Expressions for affinity. | `{}` |
| `fullnameOverride` | Override the full chart name. | `""` |
| `image.pullPolicy` | Image pull policy. | `IfNotPresent` |
| `image.repository` | Image repository. | `prom/statsd-exporter` |
| `image.tag` | Image tag. | `nil` (Use `.Chart.AppVersion`) |
| `imagePullSecrets` | Name of Secret resource containing private registry credentials. | `[]` |
| `ingress.annotations` | Ingress annotations. | `{}` |
| `ingress.enabled` | Enable Ingress. | `false` |
| `ingress.hosts` | Ingress accepted hostnames. | `[]` |
| `ingress.tls` | Ingress TLS configuration. | `[]` |
| `nameOverride` | Override the application name. | `""` |
| `nodeSelector` | Node labels for pod assignment. | `{}` |
| `podSecurityContext` | Security options for pod. | `{}` |
| `replicaCount` | Number of replica. | `1` |
| `resources` | CPU/Memory resource requests/limits. | `{}` |
| `securityContext` | Security options for container. | `{}` |
| `service.type` | Type of service to create. | `ClusterIP ` |
| `service.annotations` | Service annotations. | `{}` |
| `serviceAccount.create` | Specifies whether a service account should be created. | `true` |
| `serviceAccount.name` | Name of the service account. | |
| `serviceMonitor.additionalLabels` | Additional labels to add to the ServiceMonitor. | `{}` |
| `serviceMonitor.enabled` | Set this to `true` to create ServiceMonitor for Prometheus operator. | `true` |
| `serviceMonitor.interval` | Interval at which metrics should be scraped. | `30s` |
| `serviceMonitor.namespace` | Namespace which ServiceMonitor is installed. | `monitoring` |
| `serviceMonitor.scrapeTimeout` | Interval at which metric scrapes should time out. | `10s` |
| `statsd.cacheSize` | Maximum size of your metric mapping cache. Relies on least recently used replacement policy if max size is reached. | `1000` |
| `statsd.eventFlushThreshold` | Number of events to hold in queue before flushing. | `1000` |
| `statsd.eventFlushInterval` | Time interval before flushing events in queue. | `200ms` |
| `statsd.eventQueueSize` | Size of internal queue for processing events. | `10000` |
| `statsd.mappingConfig` | Metric mapping configuration. | |
| `statsd.tcpPort` | The TCP port on which to receive statsd metric lines. Set `""` to disable it. | `9125` |
| `statsd.udpPort` | The UDP port on which to receive statsd metric lines. Set `""` to disable it. | `9125` |
| `tolerations` | Toleration labels for pod assignment. | `[]` |
| `web.path` | Path under which to expose metrics. | `/metrics` |
| `web.port` | The address on which to expose the web interface and generated Prometheus metrics. | `9102` |

Specify each parameter using the `--set key=value[,key=value]` argument to `helm install`. For example,

```console
$ helm install my-release \
  --set serviceAccount.name=statsd-exporter  \
    hahow/prometheus-statsd-exporter
```

Alternatively, a YAML file that specifies the values for the above parameters can be provided while installing the chart. For example,

```console
$ helm install my-release -f values.yaml hahow/prometheus-statsd-exporter
```
