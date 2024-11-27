# eap-charts
Helm Charts for Red Hat JBoss Enterprise Application Platform XP 6 (JBoss EAP XP 6)

## Install Helm Repository for EAP Charts

The `eap-xp6` Chart can be installed from the [https://jbossas.github.io/eap-charts/](https://jbossas.github.io/eap-charts/) repository

```
$ helm repo add jboss https://jbossas.github.io/eap-charts/
"jboss" has been added to your repositories
$ helm search repo jboss
NAME                    CHART VERSION   APP VERSION     DESCRIPTION
jboss/eap-xp6          	1.0.0           6.0       	    Build and deploy EAP XP 6 applications on OpenShift
````

## EAP XP 6 Charts docs

* A complete documentation of the `eap81` Chart is available in [charts/eap-xp6/](./charts/eap-xp6/README.md).

## Prerequisites
Below are prerequisites that may apply to your use case.

### Pull Secret
You will need to create a pull secret if you pull the EAP S2I builder image. Use the following command as a reference to create your pull secret:
```bash
oc create secret docker-registry my-pull-secret --docker-server=registry.redhat.io --docker-username=$USERNAME --docker-password=$PASSWORD --docker-email=$EMAIL
```

You can use this secret by passing `--set build.pullSecret=my-pull-secret` to `helm install`, or you can configure this in a values file:
```yaml
build:
  pullSecret: my-pull-secret
```
and apply by passing `-f $VALUES_FILE`.

# Examples

The [examples](./examples/) directory contains examples of EAP applications deployed with Helm Charts