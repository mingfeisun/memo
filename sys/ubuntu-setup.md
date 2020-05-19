## Ubuntu System Setup

* Mingfei Sun
* Created: 2017-11-09
* Updated: 2020-05-19

### Preliminary
``` bash
sudo apt-get update
sudo apt-get install build-essential
```

### Python
``` bash
sudo apt-get install python-dev
sudo apt-get install python-pip
sudo pip install --upgrade pip
sudo pip install numpy
sudo pip install scipy
sudo pip install pandas
```

### SSH 
``` bash
sudo apt-get install openssh-server
# start service
sudo /etc/init.d/ssh start
# check status
sudo /etc/init.d/ssh status
```

### Git
``` bash
sudo apt-get install git
```

### Github SSH key
``` shell
ssh-keygen -t rsa -b 4096 -C "mingfei.sun.hk@gmail.com"
eval "$(ssh-agent -s)"
ssh-add ~/.ssh/id_rsa
gedit ~/.ssh/id_rsa.pub
```

### Hg
``` bash
sudo apt-get install mercurial
```


### Remaping
*Keyboard*
``` bash
sudo apt-get install gnome-tweak-tool
gnome-tweak-tool
```
or
``` bash
setxkbmap -layout us -option ctrl:nocaps
```
or
``` bash
sudo dpkg-reconfigure keyboard-configuration
```

*Terminal*
``` bash
echo 'set editing-mode vi' >> ~/.inputrc
echo 'set keymap vi' >> ~/.inputrc
```

*File transmission*
``` bash 
sudo apt-get install lrzsz
```

### Vim
``` bash
sudo apt-get install vim
sudo apt-get install vim-gnome
```

*Pathogen*
``` bash
# install curl first
sudo apt-get install curl

# install pathogen
mkdir -p ~/.vim/autoload ~/.vim/bundle && \
curl -LSso ~/.vim/autoload/pathogen.vim https://tpo.pe/pathogen.vim
```

*gitgutter*
``` bash
cd ~/.vim/bundle
git clone https://github.com/airblade/vim-gitgutter.git
```

*airline*
``` bash
cd ~/.vim/bundle
git clone https://github.com/vim-airline/vim-airline
```

*color*
``` bash
mkdir -p ~/.vim/colors
cd ~/.vim/colors
wget https://raw.githubusercontent.com/tomasr/molokai/master/colors/molokai.vim
```

*.vimrc*
``` bash
cd ~
wget https://raw.githubusercontent.com/mingfeisun/vim/master/.vimrc
```

*[Consolas Font](https://www.rushis.com/consolas-font-on-ubuntu/)*
``` bash 
sudo apt-get install font-manager
sudo apt-get install cabextract

set -e
set -x
mkdir -p ~/temp
cd ~/temp
wget http://download.microsoft.com/download/E/6/7/E675FFFC-2A6D-4AB0-B3EB-27C9F8C8F696/PowerPointViewer.exe
cabextract -L -F ppviewer.cab PowerPointViewer.exe
cabextract ppviewer.cab
```
> After the program runs successfully, open the temp folder on the Desktop and install the fonts using font manager application. 

### ROS
``` bash
# http://wiki.ros.org/kinetic/Installation/Ubuntu
sudo sh -c 'echo "deb http://packages.ros.org/ros/ubuntu $(lsb_release -sc) main" > /etc/apt/sources.list.d/ros-latest.list'
sudo apt-key adv --keyserver hkp://ha.pool.sks-keyservers.net:80 --recv-key 421C365BD9FF1F717815A3895523BAEEB01FA116
sudo apt-get update
sudo apt-get install ros-kinetic-desktop-full
```

*[init](http://wiki.ros.org/kinetic/Installation/Ubuntu)*
``` bash
sudo rosdep init
rosdep update
echo "source /opt/ros/kinetic/setup.bash" >> ~/.bashrc
source ~/.bashrc
```

*[building pkg](http://wiki.ros.org/kinetic/Installation/Ubuntu)*
``` bash
sudo apt-get install python-rosinstall python-rosinstall-generator python-wstool build-essential
```

*[qt for ros](http://ros-industrial.github.io/ros_qtc_plugin/_source/How-to-Install-Users.html)*
``` bash
sudo add-apt-repository ppa:levi-armstrong/qt-libraries-xenial
sudo add-apt-repository ppa:levi-armstrong/ppa
sudo apt update && sudo apt install qt59creator
sudo apt install qt57creator-plugin-ros
```

### Wubi input method
``` bash
# install
sudo apt-get install ibus-table-wubi

# initialize
killall ibus-daemon
ibus-daemon -drx
```

### PyCharm
Download link [here](https://www.jetbrains.com/pycharm-edu/download/download-thanks.html?platform=linux)

### Visual Studio 
Download link [here](https://code.visualstudio.com/download)

### SSH key setup
* Generate keys
``` bash
ssh-keygen -t rsa
```
* Copy keys to remote server
``` bash
cat .ssh/id_rsa.pub | ssh [username]@[address] 'cat >> .ssh/authorized_keys'
```
