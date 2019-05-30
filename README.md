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

##### or the easier way 

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

--- 

### __2. Nvidia driver , CUDA and cuDNN install__

__2.0 Pre-install system check__

To check TensorFlow , CUDA and cuDNN configuration ( https://www.tensorflow.org/install/source#linux)
Run the following to check each package version:
You can check your cuda version using
nvcc --version

cuDNN version using
> cat /usr/include/cudnn.h | grep CUDNN_MAJOR -A 2

tensorflow-gpu version using
> pip freeze | grep tensorflow-gpu

For current setup we installed TensorFlow-GPU = 1.13.1 , we need CUDA 10 and cuDNN 7.5

__2.1 Install CUDA10.0__

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

__2.2 To install cuDNN 7.5.0__

#### for install cuDNN into the specific CUDA folder 
NOTE: `this is important` to install specific version of cudnn into the corresponding CUDA folder for running multiple CUDA version on your machine

Install suitable cuDNN versions for each CUDA using the Library for Linux tar files
> tar -xzvf cudnn-8.0-linux-x64-v6.0.tgz

> sudo cp cuda/include/cudnn.h /usr/local/cuda-8.0/include

> sudo cp cuda/lib64/libcudnn* /usr/local/cuda-8.0/lib64

> sudo chmod a+r /usr/local/cuda-8.0/include/cudnn.h /usr/local/cuda-8.0/lib64/libcudnn*

Make sure to use the Library for Linux cuDNN packages (downloadable from [here](https://developer.nvidia.com/rdp/cudnn-download) and you need to register). If you use the installer to install these, they will not get installed in the correct location for each version of CUDA.

You can learn more cudnn install insructions from this [link](https://medium.com/@peterjussi/multicuda-multiple-versions-of-cuda-on-one-machine-4b6ccda6faae) 

---

**Alternate site for install CUDA [For references only]:**

for install nvidia driver on ubuntu 16.04 please follow this [link](https://qiita.com/spiderx_jp/items/460cd47ce0e0ff41c762)

for install cuda and cuDNN [medium_link1](https://medium.com/@zhanwenchen/install-cuda-9-2-and-cudnn-7-1-for-tensorflow-pytorch-gpu-on-ubuntu-16-04-1822ab4b2421)
, [medium_link2](https://medium.com/@zhanwenchen/install-cuda-and-cudnn-for-tensorflow-gpu-on-ubuntu-79306e4ac04e)
, [tensorflow_weblink](https://www.tensorflow.org/install/gpu)
