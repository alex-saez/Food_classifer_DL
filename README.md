# Food_classifer_DL

## Setup

### Spin up appropriate VM on GCP using gcloud CLI tool:

```
export IMAGE_FAMILY="common-cu90"
export ZONE="us-east1-c"
export INSTANCE_TYPE="n1-standard-4"
export NUM_GPUS=1

export INSTANCE_NAME="dl"

gcloud compute instances create $INSTANCE_NAME \
        --zone=$ZONE \
        --image-family=$IMAGE_FAMILY \
        --image-project=deeplearning-platform-release \
        --maintenance-policy=TERMINATE \
        --accelerator='type=nvidia-tesla-k80,count=$NUM_GPUS' \
        --machine-type=$INSTANCE_TYPE \
        --boot-disk-size=200GB \
        --metadata='install-nvidia-driver=True'
```

### ssh into the VM:
e.g.
```
gcloud compute ssh $INSTANCE_NAME
```
