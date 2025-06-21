# my umbrella chart collection

This repo contains my own currated list of umbrella charts for my personal use.

To add the repo to helm
`helm repo add zahlenhelfer https://zahlenhelfer.github.io/helm-charts`

To install the <chart-name> chart:
`helm install my-<chart-name> zahlenhelfer/<chart-name>`

To uninstall the chart:
`helm delete my-<chart-name>`

## Example

```bash
helm repo add zahlenhelfer https://zahlenhelfer.github.io/helm-charts
helm repo update
helm install my-metrics-server zahlenhelfer/metrics-server
```
