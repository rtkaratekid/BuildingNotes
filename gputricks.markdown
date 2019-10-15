# GPU Tricks for the time crunched (and pissed off) programmer
#### this better work...

### For a working tensorflow install on Xubuntu 18.04
* apt install nvidia-driver
    * check that this works with `nvidia-smi`
* Now to install cuDNN
    * [stack overflow](https://askubuntu.com/questions/767269/how-can-i-install-cudnn-on-ubuntu-16-04/767270#767270)
    * install cuda from [nvidia website](https://developer.nvidia.com/cuda-downloads)
        * verify [md5 sum](https://developer.download.nvidia.com/compute/cuda/10.1/Prod/docs3/sidebar/md5sum.txt)
        * DELETE ALL PREVIOUS CUDAS
        * `sudo sh <run script>`
        * make sure cuda is in PATH and LD_LIBRARY_PATH
        * verify with `nvcc --version`
        * [stack overflow troubleshooting](https://askubuntu.com/questions/799184/how-can-i-install-cuda-on-ubuntu-16-04)
    * Download [cuDNN](https://developer.nvidia.com/cudnn) (need a developer account, it's free)
    * `sudo cp include/cudnn.h /usr/local/cuda/include`
    * `sudo cp lib64/libcudnn* /usr/local/cuda/lib64`
    * `sudo chmod a+r /usr/local/cuda/lib64/libcudnn*`
* Now install tensorflow-gpu and keras
    * `sudo apt-get install libcupti-dev`
    * can check tensorflow builds and dependecies [here](https://www.tensorflow.org/install/source) (should probably do this first)

### For installing jupyterlab for python 2 and 3
* `sudo apt install python3-pip python3-dev`
* `pip install jupyter`
    * verify with `$jupyter notebook`

* `pip install jupyterlab`
* `jupyter-lab`



# Troubleshooting
---
### Check if keras/tensorflow recognize the gpus
* tensorflow
    * `from tensorflow.python.client import device_lib
print(device_lib.list_local_devices())`
* keras
    * `from keras import backend as K
K.tensorflow_backend._get_available_gpus()`


### For flushing the gpu memory
* check what is using gpu memory

`sudo fuser -v /dev/nvidia*`

`sudo kill -9 <pid of offending process>`

* next try:

`nvidia-smi --gpu-reset`

* if that doesn't work, then unload and reload nvidia driver:

`rmmod nvidia`

`modprobe nvidia`

### Monitor the gpu
nvidia-smi

nvidia-smi -l 1

---

# bOnUs TrIcKs!




