---
title: "Installation Guide SMO+NonRT RIC Rel. L  on Ubuntu 24.04"
---

# <center> Installation Guide SMO+NonRT RIC Rel. L  on Ubuntu 24.04 </center>

## Prerequisites
:::warning

1. OS Ubuntu 24.04
:::

## Deployment steps


### 1. Cloning dep repository IT/dep repository from gerrit
```bash=
# Latest version
cd ~
git clone https://gerrit.o-ran-sc.org/r/it/dep.git -b master --recursive
```

:::warning
:bulb: **Note:** You need to ==add the recurse sub modules flag== as some parts are git submodules pointing to existing related charts (ONAP)
:::

### 2. Run Make for k8s installer

```bash=
IP_ADDR=<ip_address>
cd dep/tools/setup_k8s
make run IP=$IP_ADDR SUDO=sudo
```
*wait until process finised

### 3. Setup ONAP/SMO Helm Charts

```bash=
cd $HOME
./dep/smo-install/scripts/layer-1/1-build-all-charts.sh
```

### 4. Deploy components
```bash=
./dep/smo-install/scripts/layer-2/2-install-oran.sh
```

### 5. Checking pod deployment status
```bash=
echo "Pods in ONAP namespace:"
kubectl get pods -n onap
echo "Pods in nonrtric namespace:"
kubectl get pods -n nonrtric
```