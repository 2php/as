---
layout: post
title: how to set up tensorflow
category: artificial intelligence
comments: true
---

## [tensorflow](https://github.com/tensorflow) - what it is

okay, no need to talk much about it as it was a famous open source artificial intelligence software invented by google.

## tensorflow - how to setup

It's really not good as in china we have been limited by the party so we can't access some resources outside the big firewall, yes we can use VPN, so follow the [install guide](http://wiki.jikexueyuan.com/project/tensorflow-zh/get_started/os_setup.html), and the way to install through [Anaconda](https://www.anaconda.com/) is the best way, luckily Anaconda was accessable even without VPN.

### setup on [windows 10](http://blog.nitishmutha.com/tensorflow/2017/01/22/TensorFlow-with-gpu-for-windows.html)

```sh
conda create -n tensorflow-gpu python=3.6.4
activate tensorflow-gpu
pip install tensorflow-gpu
git clone https://github.com/tensorflow/models.git
```

### build on [windows 10](https://medium.com/@vina.wt.chang/build-tensorflow-from-source-with-cmake-on-windows-c47ffb8e1bf7) [README](https://github.com/tensorflow/tensorflow/blob/master/tensorflow/contrib/cmake/README.md)

```sh
# run from C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Visual Studio 2017\Visual Studio Tools\VC x86_64 cmd
cd tensorflow\contrib\cmake
mkdir build
cd build
set PATH=C:\opt\cmake-3.11.1-win64-x64\bin;%PATH%
cmake .. -A x64 -DCMAKE_BUILD_TYPE=Release ^
  -DSWIG_EXECUTABLE=C:\opt\swigwin-3.0.12\swig.exe ^
  -DPYTHON_EXECUTABLE=C:/Anaconda3/envs/tensorflow-gpu/python.exe ^
  -DPYTHON_LIBRARIES=C:/Anaconda3/envs/tensorflow-gpu/libs/python36.lib ^
  -DPYTHON_INCLUDE_DIRS=C:/Anaconda3/envs/tensorflow-gpu/include ^
  -Dtensorflow_WIN_CPU_SIMD_OPTIONS=/arch:AVX2 ^
  -Dtensorflow_BUILD_SHARED_LIB=ON ^
  -DCUDA_HOST_COMPILER=cl.exe ^
  -Dtensorflow_ENABLE_GPU=ON ^
  -DCUDNN_HOME="C:\Program Files\NVIDIA GPU Computing Toolkit\CUDA\v9.0"
MSBuild /p:Configuration=Release tf_python_build_pip_package.vcxproj
MSBuild /p:Configuration=Release ALL_BUILD.vcxproj
```

### setup on [Ubuntu 16.04](https://www.linkedin.com/pulse/installing-nvidia-cuda-80-ubuntu-1604-linux-gpu-new-victor)

below step is get from the [doc](file:///C:/Program%20Files/NVIDIA%20GPU%20Computing%20Toolkit/CUDA/v9.1/doc/html/cuda-quick-start-guide/index.html#ubuntu-x86_64) after I install cuda 9.1 on windows.

* Disable the Nouveau drivers:

Create a file at /etc/modprobe.d/blacklist-nouveau.conf with the following contents:

```c 
blacklist nouveau
options nouveau modeset=0
```

* Regenerate the kernel initramfs:

```sh
sudo update-initramfs -u
```

* Reboot into runlevel 3 by temporarily adding the number "3" and the word "nomodeset" to the end of the system's kernel boot parameters.

* Run the installer silently to install with the default selections (implies acceptance of the EULA):

```sh
sudo sh cuda_<version>_linux.run --silent
```

* Create an xorg.conf file to use the NVIDIA GPU for display:

```sh
sudo nvidia-xconfig
```

* Reboot the system to load the graphical interface.

* Set up the development environment by modifying the PATH and LD_LIBRARY_PATH variables:

```sh
export PATH=/usr/local/cuda-9.1/bin${PATH:+:${PATH}}
export LD_LIBRARY_PATH=/usr/local/cuda-9.1/lib64\
                         ${LD_LIBRARY_PATH:+:${LD_LIBRARY_PATH}}
```

* Install a writable copy of the samples then build and run the nbody sample:

```sh
cuda-install-samples-9.1.sh ~
cd ~/NVIDIA_CUDA-9.1_Samples/5_Simulations/nbody
make
./nbody
```

## tensorflow - an example do object detection

This [object detection model](https://github.com/tensorflow/models/tree/master/research/object_detection) is really a good start point to have a try of tensorflow to see what it can do, it's very good. Also there are many other models that could do really a lot of things, I am planing to try them one by one if possible.

For the tool [protoc](https://github.com/google/protobuf), if ubuntu just use apt-get to install the necessary version, if win, download it from the [github](https://github.com/google/protobuf/releases/tag/v2.6.1). For ubuntu, we can build it from source code by below command.

```sh
wget https://github.com/google/protobuf/releases/download/v2.6.1/protobuf-2.6.1.tar.gz
tar xf protobuf-2.6.1.tar.gz && cd protobuf-2.6.1
./configure && make && make check && sudo make install
```

Here is a [CSDN](http://m.blog.csdn.net/xiaoxiao123jun/article/details/76605928) sample that use object detection model to process video.

## reference

[deep learning book](http://www.deeplearningbook.org/)
[octave](https://www.gnu.org/software/octave/)
[CNN](https://www.cnblogs.com/alexcai/p/5506806.html)
[Neural Networks and Deep Learning](http://neuralnetworksanddeeplearning.com/)


