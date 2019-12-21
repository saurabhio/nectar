### Linux
```
sudo apt-get update && sudo apt-get upgrade && sudo apt-get dist-upgrade && sudo apt-get autoremove


sudo apt-get install python3-pip 
pip3 install virtualenv

python3 -m virtualenv ~/env_test  # to create virtual environment, (by default it has setuptools, pip, and wheel)
source ~/env_test/bin/activate    # to use 'env_test' environment
deactivate			  # to exit any environment
In the environment, pip and pip3, python and python3 can be used interchangeably.

pip freeze > requirements.txt
pip install -r requirements.txt


curl -O https://storage.googleapis.com/golang/go1.6.linux-amd64.tar.gz
sha256sum go1.6.linux-amd64.tar.gz
echo "export PATH=$PATH:/usr/local/go/bin" >> ~/.profile
source ~/.profile


scp -i key_file.pem your_username@remotehost.edu:/remote/dir/foobar.txt /local/dir
scp foobar.txt your_username@remotehost.edu:/some/remote/directory

cp your_username@rh1.edu:/some/remote/directory/foobar.txt \
your_username@rh2.edu:/some/remote/directory/


curl -I http://domain.com


sudo iptables -L  (NAT: shares a single external IP among multiple hosts)


export PATH=$PATH:~/bin


sudo apt-get purge docker-ce
sudo rm -rf /var/lib/docker
```

### Linux Program Installation
```
tar -xjvf archive-name.tar.bz2    //or
tar -xzf archive-name.tar.gz

cd archive-name
./configure
make
sudo make install
```
