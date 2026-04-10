# Quick Start

#### Step 1: Add the NVIDIA Helm repository

```bash
helm repo add nvidia https://helm.ngc.nvidia.com/nvidia
helm repo update
```

#### Step 2: Deploy GPU Operator

```bash
$ helm search repo nvidia/gpu-operator
NAME               	CHART VERSION	APP VERSION	DESCRIPTION
nvidia/gpu-operator	v26.3.0      	v26.3.0    	NVIDIA GPU Operator creates/configures/manages ...
$

helm pull nvidia/gpu-operator

helm install --debug --dry-run --wait --generate-name -n gpu-operator --create-namespace \
--set ccManager.enabled=false \
--set cdi.enabled=true \
--set dcgmExporter.enabled=false \
--set devicePlugin.enabled=false \
--set kataSandboxDevicePlugin.enabled=false \
--set migManager.enabled=false \
--set sandboxDevicePlugin.enabled=false \
--set toolkit.enabled=false \
--set vfioManager.enabled=false \
--set vgpuDeviceManager.enabled=false \
--set driver.licensingConfig.nlsEnabled=false \
./learn/helm/gpu-operator > ./learn/build.yaml 2>&1

```
