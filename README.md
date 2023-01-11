# meow-vault
## pre-requisites
* A HashiCorp Vault instance
* A Kubernetes Cluster
* The Vault Helm Chart available to that Kubernetes Cluster
## Vault Nonsense
* https://developer.hashicorp.com/vault/tutorials/kubernetes/kubernetes-external-vault#install-the-vault-helm-chart-configured-to-address-an-external-vault
* Create a config secret with the following content:
```
{
  "image_height": "400",
  "image_placeholder": "placekitten.com",
  "image_width": "600",
  "owner": "Ben"
}
```

## OpenShift Nonsense
```
$ oc login
$ pushd build
$ oc new-build --binary --name=ngix-vault-build
$ oc start-build nginx-vault-build --from-dir=.
$ popd
$ oc create -f nginx-vault-meow.yml
```