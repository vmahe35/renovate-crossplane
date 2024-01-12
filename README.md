# renovate-crossplane

This project is used to provide [a minimal reproduction repository](https://github.com/renovatebot/renovate/blob/main/docs/development/minimal-reproductions.md) to help fix issue on Crossplane package with Renovate.

See discussion : <https://github.com/renovatebot/renovate/discussions/26578>

## Requirements

You need a K8S cluster with a local kubeconfig to have access to it.

Install Crossplane, by following [the official instructions](https://docs.crossplane.io/latest/software/install/).

Install the Crossplane Helm provider with: `kubectl apply -f provision/provider.yaml`

Launch the following command and wait for the helm provider to be `INSTALLED` and `HEALTHY` : `kubectl get pkg`

Install the Crossplane Helm provider config with: `kubectl apply -f provision/providerconfig.yaml`

Install the Crossplane Composition with the following commands:

```shell
kubectl apply -f package/definition.yaml
kubectl apply -f package/composition.yaml
```

Deploy the Crossplane Claim with this command:

```shell
kubectl apply -f provision/claim_with_helm.yaml
```
