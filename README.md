# Slurm-like Kubernetes Job submitting tools

Here are some simple scripts to submit jobs on a kubernetes cluster. The idea is that you can use the same commands as with slurm, but it will be translated into k8s job.

## Requirements:

- A working kubernetes cluster
- `jq` installed locally
- `kubectl` configured for your cluster

## Usage: 

We provide 2 versions of the scripts:
1. To submit on a raw kubernetes cluster
2. To submit on a cluster equipped with `volcano`. (https://volcano.sh/en/docs/)

You should put the scripts under your PATH and make them executable. There are some hard-codings in the scripts, you should configure them according to your cluster. For details, see each subdirectory in `./scripts`.

### Submit job

We provide `kbatch` command, which is similar to slurm's `sbatch`. The scripts are originally designed for pytorch distributed training, and some environment variables are set accordingly, you may need to modify them according to your needs.

example:
```bash
kbatch --gpus=8 --nodes=2 --output-dir=./logs ./job.sh
```

### check node status

We provide `kinfo` command, which is similar to slurm's `sinfo`. It will show the number of available nodes and gpus.

example:
```bash
kinfo
```

### cancel job

We provide `kcancle` command, which is similar to slurm's `scancel`. You can use it to cancel a running job.

example:
```bash
kcancel <job_id>
```

### check the job queue

We provide `kqueue` command, which is similar to slurm's `squeue`. It will show all jobs in the cluster and their status.

example:
```bash
kqueue
```