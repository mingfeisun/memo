## Keras Installation: Start from Scratch

* Mingfei Sun
* Created: 2017-11-09
* Updated: 2017-11-10

### 1. Install the driver for GPU:
http://www.nvidia.co.jp/Download/index.aspx

### 2. Install CUDA toolkit for GPU:
https://developer.nvidia.com/cuda-downloads
``` bash
sudo dpkg -i cuda-repo-ubuntu1604-9-0-local_9.0.176-1_amd64.deb
sudo apt-key add /var/cuda-repo-<version>/7fa2af80.pub
sudo apt-get update
```
Then *important*:
``` bash
sudo apt-get install cuda-8-0
```

### 3. Install cuDNN:
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

### 4. Set **$PATH** and **$LD_LIBRARY_PATH**
``` bash
echo 'export PATH=$PATH:/usr/local/cuda/bin' >> $HOME/.profile; source $HOME/.profile
echo 'export PATH=$PATH:/usr/local/cuda/bin' >> $HOME/.bashrc; source $HOME/.bashrc

echo 'export LD_LIBRARY_PATH=/usr/local/cuda/lib64:$LD_LIBRARY_PATH' >> ~/.profile; source ~/.profile
echo 'export LD_LIBRARY_PATH=/usr/local/cuda/lib64:$LD_LIBRARY_PATH' >> ~/.bashrc; source ~/.bashrc
```

### 5. Install TensorFlow
``` bash
sudo pip install tensorflow-gpu
```

### 6. Install Keras:
``` bash
sudo pip install keras
```

### 7. Install H5py
``` bash
sudo pip install h5py
```
or
``` bash
sudo apt-get install python-h5py
```
