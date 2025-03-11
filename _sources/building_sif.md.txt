(user_guide)=

# Building Image for Singularity

If the cluster is running an outdated Linux distro, some of the pre-built wheels might not be compatible.
As a workaround, leverage Singularity to run a more modern version of Linux within a containerized environment.

Below are instructions for building the image with uv, vLLM, TRL, and Unsloth pre-installed.

```bash
IMAGE_NAME=unsloth-vllm-trl
REVISION=0.1.0
sudo docker build --tag ${IMAGE_NAME}:${REVISION} .
sudo singularity build --nv ${IMAGE_NAME}_${REVISION}.sif docker-daemon://${IMAGE_NAME}:${REVISION}
```
