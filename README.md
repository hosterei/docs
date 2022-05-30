# Documentation of ounu.ch platform
Ounu.ch is the platform which poweres hosterei.ch / hosterei.space. It it build on hetzner hcloud. 

## Infrastrucure
### Management
All magament tools are running on a seperate kubernetes cluster. Tools are deployed with ArgoCD (app-of-apps).

**Installed Tools**
- ArgoCD (with vault plugin)
- Keycloack
- hosterei.ch backend

- prom-stack (complete)
- nginx ingress controller (incl. cert-manager)

**External Tools**
- GitLab
- Vault

### Workload
The workload is runnning on a kubernets cluster. There is no direct access to the cluster, everything which is deployed via ArgoCD from the management cluster. 



## Hosting
Users have an nice UI where there can manage thier Applications. The User workflow looks something like that:
![User flow](./User-process.drawio.png?raw=true "Userprocess")


### GitOps
**GitLab**

GitLab is used as DevOps Platform for the hole project. Also all the cutomers repositories are stored within GitLab. 

**ArgoCD**

Argocd is used to deploy the Applications automatically to the kubernets cluster. Application manifest gets generated with the ArgoCD applicationsets controller. The [SCM Provider Generator](https://argocd-applicationset.readthedocs.io/en/stable/Generators-SCM-Provider/#scm-provider-generator) will be used.

ArgoCD Image Updater is used to automatically update the applications. Git Git update stragegy which kustomize wirte-back-target is used for that. 

Addons:
  - ArgoCD applicatoinsets 
  - ArgoCD Image updater