# Recommended tmux Workflow for GPU Jobs

Start a tmux session
```bash
tmux new -s mysession
```
Request GPU resources inside tmux
```bash
salloc --partition a30 --gres=gpu:1
```
Check your allocation:
```bash
squeue -l --me
nvidia-smi  # monitor GPU usage
```
Activate Python environment and start JupyterLab
```bash
source /vol/bitbucket/lc3223/.venv/bin/activate
python -m jupyterlab --no-browser --ip=127.0.0.1 --port=8899
```
Set up SSH port forwarding (from your local machine)
```bash
ssh -N -L 8899:127.0.0.1:8899 lc3223@
```
Detach from tmux session (session keeps running in the background)
Press:
```bash
Ctrl + b  then  d
```
Reattach to tmux session (if you want to check on it later)
```bash
tmux attach -t mysession
```
Kill tmux session (when finished)
```bash
tmux kill-session -t mysession
```
