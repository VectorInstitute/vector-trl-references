---
hide-toc: true
---

# Vector AI Engineering template (uv edition) repository

```{toctree}
:hidden:

building_sif
api

```

You can override the packages using `uv` and by adjusting pyproject.toml.
If you need a custom vLLM installation, follow the `building_sif` section to build your own image.
Most user can just use the image provided on the cluster, available at:

```bash
SIF_IMAGE=/projects/llm/unsloth-vllm-trl-latest.sif
```

Run the following:

```bash
salloc -p a40 --gres gpu:1 -c 8 --mem 32GB --time 16:00:00 --job-name vllm-trl

module load singularity-ce
SIF_IMAGE=/projects/llm/unsloth-vllm-trl-latest.sif

singularity exec \
--nv \
--bind /model-weights:/model-weights \
--bind /projects/llm:/projects/llm \
--bind /scratch/ssd004/scratch/`whoami`:/scratch \
--bind /opt/slurm/:/opt/slurm/ \
${SIF_IMAGE} \
python3 /projects/llm/unsloth/examples/lora_vllm_grpo.py
```
