# kubebuilder-playground

Playground that develops custom resource definition of k8s with [kubebuilder](https://book.kubebuilder.io).

## Commands

### Install CRD

Install k8s CRD by using [kustomize](https://kustomize.io).

```bash
$ make install
${GOPATH}/bin//controller-gen "crd:trivialVersions=true" rbac:roleName=manager-role webhook paths="./..." output:crd:artifacts:config=config/crd/bases
kustomize build config/crd | kubectl apply -f -
customresourcedefinition.apiextensions.k8s.io/guestbooks.webapp.kubebuilder.kamiazya.tech created
```

### Create project

```bash
kubebuilder init --domain  kubebuilder.kamiazya.tech
```

### Create API

```bash
kubebuilder create api --group webapp --version v1 --kind Guestbook
```
