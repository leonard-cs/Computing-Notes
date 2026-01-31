# DOC GPU Cluster Setup Guide

For more detailed information, please refer to the [official Imperial College GPU Cluster Guide](https://www.imperial.ac.uk/computing/people/csg/guides/hpcomputing/gpucluster/).

## 1. SSH Configuration for GPU Cluster

First, add the following configuration to your SSH config file (`~/.ssh/config`) to simplify SSH connections:

```bash
Host gpucluster3
    HostName gpucluster3.doc.ic.ac.uk
    User lc3223
    ProxyJump shell3
    IdentityFile ~/.ssh/doc_ed25519
```
This allows you to connect to the GPU cluster using **VSCode Remote-SSH**

## 2. Set Up Directory and Virtual Environment
Once connected, create a directory for your project:
```bash
mkdir /vol/bitbucket/lc3223
cd /vol/bitbucket/lc3223
```
Then, create a Python virtual environment:
```bash
python -m virtualenv /vol/bitbucket/lc3223/.venv
```
Activate the virtual environment:
```bash
source /vol/bitbucket/lc3223/.venv/bin/activate
```

## 3. Install JupyterLab
To install JupyterLab, run the following command:
```bash
pip install jupyterlab
```

## 4. Request GPU Resources
To request GPU resources, use the salloc command:
```bash
salloc --gres=gpu:1
```
To specify a partition, use the following command:
```bash
salloc --partition a30
```
Check your job status:
```bash
squeue -l --me
```
You can also monitor GPU usage with nvidia-smi:
```bash
nvidia-smi
```

## 5. Access JupyterLab Remotely
To access JupyterLab on the cluster remotely, create an SSH tunnel to forward the JupyterLab port (default is 8899):
```bash
ssh -N -L 8899:127.0.0.1:8899 lc3223@<machine_name>
```
Then, start JupyterLab:
```bash
source /vol/bitbucket/lc3223/.venv/bin/activate
python -m jupyterlab --no-browser --ip=127.0.0.1 --port=8899
```
Finally, connect to the Jupyter kernel running on the cluster.
1. Click on the **Kernel** in the top-right corner of the notebook and choose **Select Another Kernel**.
2. Paste the link and select the kernel running on `127.0.0.1`.

## 6. Cancel Job
To cancel a running job, use the following command:
```bash
scancel <job ID>
```
