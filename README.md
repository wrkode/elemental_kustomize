# Elemental-Kustomize

***
This repository contains the kustomizations required to create a Rancher Elemental ```Registration Endpoint``` and the ```SeedImage``` for it.

## Fleet

Fleet is the Continuos Delivery solution of Rancher.
Fleet is being used to streamline and use proper GitOps methodologies for Elemental image life cycle managment.

## Usage

Thses are the high-level steps.

- Fork this repository to your Git Solution.
- Edit ```base/endpoint.yaml```, ```base/name_patch.yaml``` and ```overlays/cloud-config.yaml```.
- create a ```GitRepo``` resource in **Rancher Continuos Delivery**.
- Observe the creation and operation of the ```GitRepo``` resource.
- Veryify in **Rancher OS Management** a **Registration Endpoint** and the **SeedImage** is created with the desired parameters.

## Fleet GitRepo

For the creation of the GitRepo Resource refer to this manifest:

```yaml
apiVersion: fleet.cattle.io/v1alpha1
kind: GitRepo
metadata:
  name: elemental-kustomize
  namespace: fleet-local
spec:
  branch: main
  correctDrift:
    enabled: true
  insecureSkipTLSVerify: false
  repo: https://link.to.your/repo
  targets: []
```

- Use ```kubectl apply -f``` to apply this manifest to the Rancher Manager Cluster.
