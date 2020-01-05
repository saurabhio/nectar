### Linux
```
sudo apt-get update && sudo apt-get upgrade && sudo apt-get dist-upgrade && sudo apt-get autoremove

curl -O https://storage.googleapis.com/golang/go1.6.linux-amd64.tar.gz
sha256sum go1.6.linux-amd64.tar.gz
echo "export PATH=$PATH:/usr/local/go/bin" >> ~/.profile
source ~/.profile


uname -a
lsb_release -a
cat /etc/lsb-release
cat /etc/issue



sudo useradd -m -p $(openssl passwd -crypt saurabh) saurabh


curl -I http://domain.com


sudo iptables -L  (NAT: shares a single external IP among multiple hosts)


export PATH=$PATH:~/bin


sudo apt-get purge docker-ce
sudo rm -rf /var/lib/docker


unzip     1.zip
tar -xvf  1.tar      
tar -xvf  1.tar.xz   
tar -jxvf 1.tbz2     
tar -jxvf 1.tar.bz2 
tar -zxvf 1.tgz
tar -zxvf 1.tar.gz  
7z   x    1.rar  
7z   x    1.7z      
bunzip2   1.bz2      
gunzip    1.gz   


grep hosts /abc/*  1>   output.txt //error on console (default)
grep hosts /abc/*  2>   error.txt  //output on console
grep hosts /abc/*  2&1> both.txt   //nothing on console



apt-get remove [--auto-remove] httpie
apt-get purge  [--auto-remove] httpie


find ~/Downloads/ -type f -print0 | xargs -0 mv -t ~/Videos


#!/bin/bash
for file in ./16/*.txt; do
    cat $file >> 16.txt
    printf '\n\n---------------------------------------------------------------\n\n' >> 16.txt
done


#!/bin/bash
for file in *.jpg.txt; do
    mv "$file" "$(basename "$file" .jpg.txt).docx"
done


```


```
# File sharing
python -m http.server 2020
wget -pcmkEe robots=off 192.168.1.2:2020
```

### Linux Program Installation
```
tar -jxvf archive-name.tar.bz2    //or
tar -zxvf archive-name.tar.gz

cd archive-name
./configure
make
sudo make install
```
