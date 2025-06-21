# metrics-server

![Version: 0.2.1](https://img.shields.io/badge/Version-0.2.1-informational?style=flat-square) ![Type: application](https://img.shields.io/badge/Type-application-informational?style=flat-square)

Umbrella chart - Metrics Server

## Requirements

| Repository | Name | Version |
|------------|------|---------|
| https://kubernetes-sigs.github.io/metrics-server/ | metrics-server | 3.12.2 |

## Values

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| metrics-server.addonResizer.enabled | bool | `false` |  |
| metrics-server.addonResizer.image.repository | string | `"registry.k8s.io/autoscaling/addon-resizer"` |  |
| metrics-server.addonResizer.image.tag | string | `"1.8.21"` |  |
| metrics-server.addonResizer.nanny.cpu | string | `"0m"` |  |
| metrics-server.addonResizer.nanny.extraCpu | string | `"1m"` |  |
| metrics-server.addonResizer.nanny.extraMemory | string | `"2Mi"` |  |
| metrics-server.addonResizer.nanny.memory | string | `"0Mi"` |  |
| metrics-server.addonResizer.nanny.minClusterSize | int | `100` |  |
| metrics-server.addonResizer.nanny.pollPeriod | int | `300000` |  |
| metrics-server.addonResizer.nanny.threshold | int | `5` |  |
| metrics-server.addonResizer.resources.limits.cpu | string | `"40m"` |  |
| metrics-server.addonResizer.resources.limits.memory | string | `"25Mi"` |  |
| metrics-server.addonResizer.resources.requests.cpu | string | `"40m"` |  |
| metrics-server.addonResizer.resources.requests.memory | string | `"25Mi"` |  |
| metrics-server.addonResizer.securityContext.allowPrivilegeEscalation | bool | `false` |  |
| metrics-server.addonResizer.securityContext.capabilities.drop[0] | string | `"ALL"` |  |
| metrics-server.addonResizer.securityContext.readOnlyRootFilesystem | bool | `true` |  |
| metrics-server.addonResizer.securityContext.runAsNonRoot | bool | `true` |  |
| metrics-server.addonResizer.securityContext.runAsUser | int | `1000` |  |
| metrics-server.addonResizer.securityContext.seccompProfile.type | string | `"RuntimeDefault"` |  |
| metrics-server.affinity | object | `{}` |  |
| metrics-server.apiService.annotations | object | `{}` |  |
| metrics-server.apiService.caBundle | string | `""` |  |
| metrics-server.apiService.create | bool | `true` |  |
| metrics-server.apiService.insecureSkipTLSVerify | bool | `true` |  |
| metrics-server.args | list | `[]` |  |
| metrics-server.commonLabels | object | `{}` |  |
| metrics-server.containerPort | int | `10250` |  |
| metrics-server.defaultArgs[0] | string | `"--cert-dir=/tmp"` |  |
| metrics-server.defaultArgs[1] | string | `"--kubelet-preferred-address-types=InternalIP,ExternalIP,Hostname"` |  |
| metrics-server.defaultArgs[2] | string | `"--kubelet-use-node-status-port"` |  |
| metrics-server.defaultArgs[3] | string | `"--metric-resolution=15s"` |  |
| metrics-server.deploymentAnnotations | object | `{}` |  |
| metrics-server.dnsConfig | object | `{}` |  |
| metrics-server.extraVolumeMounts | list | `[]` |  |
| metrics-server.extraVolumes | list | `[]` |  |
| metrics-server.fullnameOverride | string | `""` |  |
| metrics-server.hostNetwork.enabled | bool | `false` |  |
| metrics-server.image.pullPolicy | string | `"IfNotPresent"` |  |
| metrics-server.image.repository | string | `"registry.k8s.io/metrics-server/metrics-server"` |  |
| metrics-server.image.tag | string | `""` |  |
| metrics-server.imagePullSecrets | list | `[]` |  |
| metrics-server.livenessProbe.failureThreshold | int | `3` |  |
| metrics-server.livenessProbe.httpGet.path | string | `"/livez"` |  |
| metrics-server.livenessProbe.httpGet.port | string | `"https"` |  |
| metrics-server.livenessProbe.httpGet.scheme | string | `"HTTPS"` |  |
| metrics-server.livenessProbe.initialDelaySeconds | int | `0` |  |
| metrics-server.livenessProbe.periodSeconds | int | `10` |  |
| metrics-server.metrics.enabled | bool | `false` |  |
| metrics-server.nameOverride | string | `""` |  |
| metrics-server.nodeSelector | object | `{}` |  |
| metrics-server.podAnnotations | object | `{}` |  |
| metrics-server.podDisruptionBudget.enabled | bool | `false` |  |
| metrics-server.podDisruptionBudget.maxUnavailable | string | `nil` |  |
| metrics-server.podDisruptionBudget.minAvailable | string | `nil` |  |
| metrics-server.podLabels | object | `{}` |  |
| metrics-server.podSecurityContext | object | `{}` |  |
| metrics-server.priorityClassName | string | `"system-cluster-critical"` |  |
| metrics-server.rbac.create | bool | `true` |  |
| metrics-server.rbac.pspEnabled | bool | `false` |  |
| metrics-server.readinessProbe.failureThreshold | int | `3` |  |
| metrics-server.readinessProbe.httpGet.path | string | `"/readyz"` |  |
| metrics-server.readinessProbe.httpGet.port | string | `"https"` |  |
| metrics-server.readinessProbe.httpGet.scheme | string | `"HTTPS"` |  |
| metrics-server.readinessProbe.initialDelaySeconds | int | `20` |  |
| metrics-server.readinessProbe.periodSeconds | int | `10` |  |
| metrics-server.replicas | int | `1` |  |
| metrics-server.resources.requests.cpu | string | `"100m"` |  |
| metrics-server.resources.requests.memory | string | `"200Mi"` |  |
| metrics-server.revisionHistoryLimit | string | `nil` |  |
| metrics-server.schedulerName | string | `""` |  |
| metrics-server.securityContext.allowPrivilegeEscalation | bool | `false` |  |
| metrics-server.securityContext.capabilities.drop[0] | string | `"ALL"` |  |
| metrics-server.securityContext.readOnlyRootFilesystem | bool | `true` |  |
| metrics-server.securityContext.runAsNonRoot | bool | `true` |  |
| metrics-server.securityContext.runAsUser | int | `1000` |  |
| metrics-server.securityContext.seccompProfile.type | string | `"RuntimeDefault"` |  |
| metrics-server.service.annotations | object | `{}` |  |
| metrics-server.service.labels | object | `{}` |  |
| metrics-server.service.port | int | `443` |  |
| metrics-server.service.type | string | `"ClusterIP"` |  |
| metrics-server.serviceAccount.annotations | object | `{}` |  |
| metrics-server.serviceAccount.create | bool | `true` |  |
| metrics-server.serviceAccount.name | string | `""` |  |
| metrics-server.serviceAccount.secrets | list | `[]` |  |
| metrics-server.serviceMonitor.additionalLabels | object | `{}` |  |
| metrics-server.serviceMonitor.enabled | bool | `false` |  |
| metrics-server.serviceMonitor.interval | string | `"1m"` |  |
| metrics-server.serviceMonitor.metricRelabelings | list | `[]` |  |
| metrics-server.serviceMonitor.relabelings | list | `[]` |  |
| metrics-server.serviceMonitor.scrapeTimeout | string | `"10s"` |  |
| metrics-server.tmpVolume.emptyDir | object | `{}` |  |
| metrics-server.tolerations | list | `[]` |  |
| metrics-server.topologySpreadConstraints | list | `[]` |  |
| metrics-server.updateStrategy | object | `{}` |  |

----------------------------------------------
Autogenerated from chart metadata using [helm-docs v1.14.2](https://github.com/norwoodj/helm-docs/releases/v1.14.2)
