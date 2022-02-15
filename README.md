# Ray Trainer

## Ubuntu Cluster Environment Prepare

### Install CUDA and CUDNN

```bash
cuda 11.3
```

### Install Anaconda

## Install

### Create Same Python Environment

```bash
sudo apt install awscli
conda create env -n ray python=3.8
conda activate ray
pip install "ray[rllib]" "gym[atari]" "gym[accept-rom-license]" atari_py opencv-python
pip install torch==1.10.2+cu113 torchvision==0.11.3+cu113 torchaudio==0.10.2+cu113 -f https://download.pytorch.org/whl/cu113/torch_stable.html
```

run this on all pc and make sure that all versions listed are the same
```bash
pip list | grep -E "ray|torch|boto3"
```

## Start Cluster

### Start Client

run this on your client pc for running code later

```bash
conda activate ray
ray start --head --port=<target-port>
```

it will give you an redis-password, use it on all your server pc

### Start all Server

run this on all your server pc

```bash
conda activate ray
ray start --address=<client-pc-ip>:<target-port> --redis-password=<your-redis-password>
```

## Run your code

add this to your code and run

```bash
ray.init(address="auto")
```

## Stop Server

run this on your server pc

```bash
ray stop
```

## Enjoy it~

