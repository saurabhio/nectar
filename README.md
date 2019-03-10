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

### Miniconda
```
conda install -y pip numpy scipy pandas scikit-learn matplotlib seaborn plotly nltk Pillow jupyter
conda install -y tensorflow keras
```

### File sharing
```
python -m http.server 2020

wget -pcmkEe robots=off 192.168.1.2:2020
```

### Linux
```
sudo apt-get update && sudo apt-get upgrade && sudo apt-get dist-upgrade && sudo apt-get autoremove

sudo apt-get install python3 python3-pip python3-dev python-virtualenv 
sudo pip3 install numpy scipy matplotlib pandas scikit-learn tensorflow keras -U


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
ssh -v -i ~/Downloads/aws-dl.pem ubuntu@52.42.90.161
scp -i ~/Downloads/aws-dL.pem -r ~/Desktop/install.sh ubuntu@52.42.90.161:~/.

chmod +x install.sh

e.g. ssh -p 22000 saurabh@192.168.3.117
```

Workflow:

- SSH into your aws instance.
- Create a new tmux session called work using the command tmux new -s work.
- Do everything as you would previously.
- Detach from the session by pressing ctrl-b followed by d.

- Once you’ve detached yourself from the session, you can work on anything else, even go to sleep.
- Subsequently, if you need to reattach to that particular tmux session to check your progress, run ```tmux a -t work```


### REST APIs

PUT:
```
$ curl http://localhost:5000/todos/todo3 -d "task=something different" -X PUT -v
requests.put('http://localhost:5000/todos/todo3', data={'task': 'Remember the milk'}).json()
```

DELETE:
```
$ curl http://localhost:5000/todos/todo1 -X DELETE -v
requests.delete('http://localhost:5000/todos/todo1')
```

UPDATE: 
```
$ curl http://localhost:5000/todos/todo3 -d "task=Remember the water" -X PUT -v
requests.put('http://localhost:5000/todos/todo3', data={'task': 'Remember the water'}).json()
```

POST:
```
$ curl http://localhost:5000/todos -d "task=Remember the milk" -X POST -v
requests.post('http://localhost:5000/todos', data={'task': 'Remember the milk'}).json()
```

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

### Sitemap
```
https://www.google.com/ping?sitemap=https://www.example.com/sitemap.xml
```

