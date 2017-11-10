## Ubuntu System Setup

* Mingfei Sun
* Created: 2017-11-09
* Updated: 2017-11-09

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

### Git
``` bash
sudo apt-get install git
```


### Remaping
*Keyboard*
``` bash
sudo apt-get install gnome-tweak-tool
gnome-tweak-tool
```

*Terminal*
``` bash
echo 'set editing-mode vi' >> ~/.inputrc
echo 'set keymap vi' >> ~/.inputrc
```

### Vim
``` bash
sudo apt-get install vim
sudo apt-get install vim-gnome
```

*Pathogen*
``` bash
# install
mkdir -p ~/.vim/autoload ~/.vim/bundle && \
curl -LSso ~/.vim/autoload/pathogen.vim https://tpo.pe/pathogen.vim
```

*gitgutter*
``` bash
cd ~/.vim/bundle
git clone git://github.com/airblade/vim-gitgutter.git
```

*airline*
``` bash
cd ~/.vim/bundle
git clone https://github.com/vim-airline/vim-airline
```

*color*
``` bash
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
mkdir temp
cd temp
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
