# Organizr Helm Chart

Baseline Helm chart for [Organizr](https://organizr.app) — an HTPC/homelab dashboard. Uses the [bjw-s app-template](https://github.com/bjw-s/helm-charts) (alias `organizr`) and [organizr-tab-controller](https://github.com/expectedbehaviors/organizr-tab-controller) for annotation-driven tab sync.

## Subcharts

| Subchart | Source | Values prefix | Description |
|----------|--------|---------------|-------------|
| **organizr** (app-template) | [bjw-s helm-charts](https://github.com/bjw-s/helm-charts) | `organizr.*` | Deployment, ingress, Theme.Park env, persistence. |
| **organizr-tab-controller** | [organizr-tab-controller](https://github.com/expectedbehaviors/organizr-tab-controller) | `organizr-tab-controller.*` | Tab sync from cluster annotations; HPA and leader election. |

## Configuration

Override ingress hosts, persistence (`size` / `existingClaim`), Theme.Park settings, and the controller API secret (`organizr-api` / `api_key` by default).

## Install

```bash
helm repo add bjw-s https://bjw-s-labs.github.io/helm-charts
helm repo add otc https://expectedbehaviors.github.io/organizr-tab-controller
helm dependency update .
helm template release . -f values.yaml
```

## Support this project

I build tools to get the best homelab experience I can from what's available and to grow as a programmer along the way. If you'd like to contribute, donations go toward homelab operating costs and subscriptions that keep this tooling maintained. Optional and appreciated.

[![Donate with PayPal](https://www.paypalobjects.com/en_US/i/btn/btn_donate_LG.gif)](https://www.paypal.com/donate/?business=9RHVW92WMWQNL&no_recurring=0&item_name=Optional+donations+help+support+Expected+Behaviors%E2%80%99+open+source+work.+Thank+you.&currency_code=USD)
