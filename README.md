# analytics-platform-charts

Contains the manifest for all applications installed into the Analytics Platform kubernetes cluster.

## Chart Structure

### platform

System level applications necessary for cluster setup.  Typically only touched by the platform team.

* nginx-ingress
* auto-scaler
* external-dns

### apps

Team applications.  This is where a team would add their new application usually.

* sample-app

Typically to add your own app you need to perform these steps:

1. Copy the `chart/templates/sample.yaml` into `chart/templates`, change the values `.Values.sample` to `.Values.myapp`
1. Copy the `sample` section to `chart/values.yaml` with your appname e.g. `myapp`, change the values to point to your helm repo
1. Create a PR/git push these changes, ArgoCD will pick them up automatically once merged to master