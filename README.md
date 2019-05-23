# Installation_guide_for_TF_CUDA
This is an installation guide for TensorFlow 1.13 with CUDA 10.0 on Ubuntu 16.04
---
### __1. Virtual Environment setup__

follow the guide inside [here](https://www.tensorflow.org/install/pip?lang=python2) to Create virtualenv

$ virtualenv --system-site-packages -p python2.7 ./virtual_environment_name
$ source ./venv/bin/activate
$ pip install --upgrade pip
$ pip list
$ deactivate

$ pip install --upgrade tensorflow

## OR

##### for `python2`

> virtualenv -p python pytorch-env

##### for  `python 3`

check python3 folder location
> which python3

check python3 version
> python3 -V

> virtualenv -p /usr/bin/python3 my_project

to activate virtualenv

> source my_project/bin/activate

[learn more](https://help.dreamhost.com/hc/en-us/articles/115000695551-Installing-and-using-virtualenv-with-Python-3) about virtual env



__NOTE:__ if there are missing packages errors, use
> pip install package_name

Check tensorflow installed correctly inside virtualenv run the following after sourcing virtualenv
> source ~/environment/virtual_environment_name/bin/activate

> python

> import tensorflow

> tensorflow.__version__

### __2 Nvidia driver , CUDA and cuDNN install__

__Pre-install system check__

To check TensorFlow , CUDA and cuDNN configuration ( https://www.tensorflow.org/install/source#linux)
Run the following to check each package version:
You can check your cuda version using
nvcc --version

cuDNN version using
> cat /usr/include/cudnn.h | grep CUDNN_MAJOR -A 2

tensorflow-gpu version using
> pip freeze | grep tensorflow-gpu

For current setup we installed TensorFlow-GPU = 1.13.1 , we need CUDA 10 and cuDNN 7.5

__Install CUDA10.0__

nvidia-smi 410.78 , CUDA 10.0

Direct install CUDA and nvidia driver [pkg_dl_link](https://developer.nvidia.com/cuda-downloads?target_os=Linux&target_arch=x86_64&target_distro=Ubuntu&target_version=1604&target_type=runfilelocal)
- Operating System: Linux
- Architecture: x86_64
- Distribution: Ubuntu
- Version: 16.04
- Install Type: runfile(local)

Run the following Installation Instructions at the downloaded file location:
> sudo sh cuda_10.1.105_418.39_linux.run

Follow the command-line prompts to install CUDA

__To install cuDNN 7.5.0__

Please reference to [Qiita_link](https://qiita.com/yukoba/items/4733e8602fa4acabcc35)

__NOTE:__ You need to change the link address and file name according to your setup

>echo "deb https://developer.download.nvidia.com/compute/machine-learning/repos/ubuntu1604/x86_64 /" | sudo tee /etc/apt/sources.list.d/nvidia-ml.list

>sudo apt update

>sudo apt install libcudnn7-dev=7.5.0.56-1+cuda10.1

---

**Alternate site for install CUDA [For references only]:**

for install nvidia driver on ubuntu 16.04 please follow this [link](https://qiita.com/spiderx_jp/items/460cd47ce0e0ff41c762)

for install cuda and cuDNN [medium_link1](https://medium.com/@zhanwenchen/install-cuda-9-2-and-cudnn-7-1-for-tensorflow-pytorch-gpu-on-ubuntu-16-04-1822ab4b2421)
, [medium_link2](https://medium.com/@zhanwenchen/install-cuda-and-cudnn-for-tensorflow-gpu-on-ubuntu-79306e4ac04e)
, [tensorflow_weblink](https://www.tensorflow.org/install/gpu)
