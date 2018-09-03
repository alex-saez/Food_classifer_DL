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
### Install Anaconda and create environment:
```
export ANACONDA_URL=https://repo.anaconda.com/archive/Anaconda3-5.2.0-Linux-x86_64.sh
export ANACONDA_INSTALLER=anaconda_installer.sh
wget $ANACONDA_URL -O $ANACONDA_INSTALLER
chmod +x $ANACONDA_INSTALLER
./$ANACONDA_INSTALLER -b
echo "export PATH=$PATH:$HOME/anaconda3/bin" >> $HOME/.bashrc
source $HOME/.bashrc

conda create -n tf_p36 -y python=3.6
```
