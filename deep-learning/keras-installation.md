## Keras Installation: Start from Scratch

* Mingfei Sun
* Created: 2017-11-09
* Updated: 2017-12-01

### 1. Install the driver & CUDA toolkit for GPU:
https://developer.nvidia.com/cuda-downloads
``` bash
sudo dpkg -i cuda-repo-ubuntu1604-8-0-local_8.0.61-1_amd64.deb
sudo apt-get update
```
Then *important*:
``` bash
sudo apt-get install cuda-8-0
```

### 2. Install cuDNN:
https://developer.nvidia.com/rdp/cudnn-download

*Membership Info*:
> username: mingfei.sun.hk@gmail.com
> 
> password: Sun123457

Select: Download cuDNN v6.0. After tar, copy files to the right directory:
``` bash
cp include/* /usr/local/cuda/include
cp lib64/* /usr/local/cuda/lib64
```

### 3. Set **$PATH** and **$LD_LIBRARY_PATH**
``` bash
echo 'export PATH=$PATH:/usr/local/cuda/bin' >> $HOME/.profile; source $HOME/.profile
echo 'export PATH=$PATH:/usr/local/cuda/bin' >> $HOME/.bashrc; source $HOME/.bashrc

echo 'export LD_LIBRARY_PATH=/usr/local/cuda/lib64:$LD_LIBRARY_PATH' >> ~/.profile; source ~/.profile
echo 'export LD_LIBRARY_PATH=/usr/local/cuda/lib64:$LD_LIBRARY_PATH' >> ~/.bashrc; source ~/.bashrc
```

### 4. Install TensorFlow
``` bash
sudo pip install tensorflow-gpu
```

### 5. Install Keras:
``` bash
sudo pip install keras
# install a specific Keras
# sudo pip install keras==2.0.8
```

### 6. Install H5py
``` bash
sudo pip install h5py
```
or
``` bash
sudo apt-get install python-h5py
```
