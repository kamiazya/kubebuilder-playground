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

### Apply Sample Resource

```bash
# apply
$ kubectl apply -f config/samples/webapp_v1_guestbook.yaml
guestbook.webapp.kubebuilder.kamiazya.tech/guestbook-sample created
```

### Get and Describe Resource

```bash
# get
$ kubectl get guestbook
NAME               AGE
guestbook-sample   2m47s
$ kubectl describe guestbook guestbook-sample
Name:         guestbook-sample
Namespace:    default
Labels:       <none>
Annotations:  kubectl.kubernetes.io/last-applied-configuration:
                {"apiVersion":"webapp.kubebuilder.kamiazya.tech/v1","kind":"Guestbook","metadata":{"annotations":{},"name":"guestbook-sample","namespace":...
API Version:  webapp.kubebuilder.kamiazya.tech/v1
Kind:         Guestbook
Metadata:
  Creation Timestamp:  2019-10-29T11:58:55Z
  Generation:          1
  Resource Version:    100219
  Self Link:           /apis/webapp.kubebuilder.kamiazya.tech/v1/namespaces/default/guestbooks/guestbook-sample
  UID:                 57d25e09-2a8f-40ad-9bd5-5444a610f23c
Spec:
  Foo:   bar
Events:  <none>
```
