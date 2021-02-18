# Asterisk installation in ubuntu

## Change user
    sudo su
    
## Update packages and Reboot the device
    sudo apt update
    sudo reboot
    
## Install required packege
    sudo apt -y install git curl wget libnewt-dev libssl-dev libncurses5-dev subversion  libsqlite3-dev build-essential libjansson-dev libxml2-dev  uuid-dev

## Add universe repository and install subversion
    sudo add-apt-repository universe
    
## Update all package
    sudo apt update
    
## go to root directory
    cd


## check asterisk policy
    sudo apt policy asterisk
    
## install another required package
    sudo apt-get update
    sudo apt-get install build-essential

## Download asterisk(18)
    wget http://downloads.asterisk.org/pub/telephony/asterisk/asterisk-18-current.tar.gz
    
## check in directory that asterisk downloaded
    ls
## output for me
    asterisk-18-current.tar.gz  snap
    
## extract the file
    tar zxvf asterisk-18-current.tar.gz
    
## check directory for new extracted folder name
    ls
    
## output for me
    asterisk-18-current.tar.gz  asterisk-18.2.0 snap
    
## change directory and enter into the new extracted folder
    cd asterisk-18.2.0
    
## update all packages
    sudo apt-get update
    
## Configure asterisk
    ./configure
    
# if the configuration does not complete then install another packages

## install libedit
    sudo apt-get install libedit
    sudo apt-get install libedit-dev
    
## install uuid
    sudo apt install uuid-dev
    
##install libjansson
    sudo apt-get install libjansson-dev
    
## install libxml2
    sudo apt install libxml2
    sudo apt install libxml2-dev
   
## install sqlite3
    sudo apt intall sqlite3
    sudo apt intall libsqlite3-dev
    
## update all packages
    sudo apt update
    
## configure asterisk now
    ./configure

## make config
    make menuconfig
    
## if you see any new window poped up, just exit(use arrow to move and enter)
    make
    make install
    
## confirm your current directory is /asterisk-18.2.0
    make simples
    
## asterisk installation is done... check asterisk version using
    asterisk -V
    
    



