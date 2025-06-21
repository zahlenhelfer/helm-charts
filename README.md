# my umbrella chart collection

[![Dependabot Updates](https://github.com/zahlenhelfer/helm-charts/actions/workflows/dependabot/dependabot-updates/badge.svg)](https://github.com/zahlenhelfer/helm-charts/actions/workflows/dependabot/dependabot-updates) [![Release Charts](https://github.com/zahlenhelfer/helm-charts/actions/workflows/release-charts.yaml/badge.svg)](https://github.com/zahlenhelfer/helm-charts/actions/workflows/release-charts.yaml) [![Generate Charts README](https://github.com/zahlenhelfer/helm-charts/actions/workflows/create-readme.yaml/badge.svg)](https://github.com/zahlenhelfer/helm-charts/actions/workflows/create-readme.yaml)

This repo contains my own currated list of umbrella charts for my personal use.

## How to `helm` this repo

To add the repo to helm
`helm repo add zahlenhelfer https://zahlenhelfer.github.io/helm-charts`

To install the chart-name chart:
`helm install my-chart-name zahlenhelfer/chart-name`

To uninstall the chart:
`helm delete my-chart-name`

## Example usage of a chart

```bash
helm repo add zahlenhelfer https://zahlenhelfer.github.io/helm-charts
helm repo update
helm install my-metrics-server zahlenhelfer/metrics-server
```
