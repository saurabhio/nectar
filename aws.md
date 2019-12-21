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

