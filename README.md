# nectar
Some useful commands, codes, etc.


### MongoDB Installation
1. Download & Install MongoDB Community Edition
2. Make following folder structure in any drive, say D:,
```
-MongoDB
	-data
		-db
		-log
			-mongo.log
	-mongod.cfg
```
3. In monod.cfg file write this:
```
dbpath=D:\MongoDB\data\db
logpath=D:\MongoDB\data\log\mongo.log
```
4. Start MongoDB service:  ```net start MongoDB```  (listens on port 27017)
5. Install MongoDB: ```mongod --config "D:\MongoDB\mongod.cfg" --install```
6. Now, to run MongoDB client: ```mongo```
7. To stop MongoDB service:  ```net stop MongoDB``` 
8. To remove MongoDB service: ```mongod --remove```

### MongoDB Import & Export
```
mongodump /h abc.def.mongolab.com /port 46719  /u username /p password123  /d dbname /o e:\MongodbBackup
mongodump -d dbname -o e:\MongodbBackup

mongorestore e:\MongodbBackup
mongorestore --db dbname E:\path\to\database\backup

mongoexport --db dbname --collection clname --type=csv --fieldFile fields.txt --out clname.csv
mongoexport --db dbname --collection clname --type=json --fieldFile fields.txt --out clname.json --pretty

bsondump --outFile abc.json abc.bson
mongoimport -d dbname -c clname abc.json
```

### WLAN
```
netsh wlan set hostednetwork mode=allow ssid=anyname key=12345678
netsh wlan start hostednetwork

netsh wlan stop hostednetwork
netsh wlan show hostednetwork
```

### File sharing
```
python -m http.server 2020

wget -pcmkEe robots=off 192.168.1.2:2020
```

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

### AWS 

After sshing into ec2 instance:
```
sudo yum update -y
sudo yum install -y docker

sudo service docker start
sudo usermod -aG docker ec2-user
```
Log out and log back in again to pick up the new docker group permissions. 

Two important commands:

- SSH into an instance
```
ssh -v -i <path to pem file> ubuntu@<Public IP>
```

- Copy file from local computer to instance
```
scp -i <path to pem file> -r <path to local file (sh)> ubuntu@<Public IP>:<path to destination on aws instance>
```

```
chmod 600 ~/Downloads/aws-dl.pem
ssh -v -i ~/Downloads/aws-dl.pem ubuntu@12.34.56.78
scp -i ~/Downloads/aws-dL.pem -r ~/Desktop/install.sh ubuntu@12.34.56.78:~/.

chmod +x install.sh

e.g. ssh -p 22000 saurabh@192.168.1.3
```

Workflow:

- SSH into your aws instance.
- Create a new tmux session called work using the command tmux new -s work.
- Do everything as you would previously.
- Detach from the session by pressing ctrl-b followed by d.

- Once you’ve detached yourself from the session, you can work on anything else, even go to sleep.
- Subsequently, if you need to reattach to that particular tmux session to check your progress, run ```tmux a -t work```


### API Example

Some examples of how users can access your API so that they can get predictions
```
url = 'http://127.0.0.1:5000/'
params ={'query': 'that movie was boring'}
response = requests.get(url, params)
response.json()
```
{'confidence': 0.128, 'prediction': 'Negative'}

```
$ curl -X GET http://127.0.0.1:5000/ -d query='that movie was boring'
```
{
    "prediction": "Negative",
    "confidence": 0.128
}

```
$ http http://127.0.0.1:5000/ query=='that movie was boring'
```
HTTP/1.0 200 OK 
Content-Length: 58  
Content-Type: application/json 
Date: Fri, 31 Aug 2018 18:49:25 GMT 
Server: Werkzeug/0.14.1 Python/3.6.3 
{
  "confidence": 0.128,
  "prediction": "Negative"
 }

### Email Authenticity

Open Original Message of the email,

- In **Received field**, check domain name and IP address 
- In **Received-SPF** field, check pass
- In **Authentication-Results** field, check **spf=pass** and **dkim=pass**

### Sitemap
```
https://www.google.com/ping?sitemap=https://www.example.com/sitemap.xml
https://www.bing.com/ping?sitemap=https://www.example.com/sitemap.xml
```

