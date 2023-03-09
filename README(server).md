# README file for the server
## How to run the server
1. Create a sandbox inside the target VM
2. Migrate into the sandbox and run the followings
```
$ wget https://raw.githubusercontent.com/jhu-information-security-institute/NwSec/master/applications/websvr/websvr-UbuntuServerX86-64.sh
$ chmod +x websvr-UbuntuServerX86-64.sh
$ ./websvr-UbuntuServerX86-64.sh
```
4. Migrate into the inner folder
5. Manually replace the existing index.html with the index.html provided by our group and replace the existing Dockerfile with Dockerfile.server we provided
6. Run and build the container
```
docker build -t websvr .
docker run -d --name websvr --hostname nginx --add-host nginx.netsec-docker.isi.jhu.edu:127.0.1.1 --dns 192.168.25.10 --dns-search netsec-docker.isi.jhu.edu --privileged -p 8080:23 -p 8000:81 --cpus=1 twebsvr:latest
docker exec -it websvr bash
```
8. Enable the server using: ```$ sudo systemctl enable nginx```

## Some notes to people who set up the server
1. Don't forget to substitute existing Dockerfile and index.html with the correct ones
2. After running the container, go to the bash and manually put the provided hint.txt under ~/
3. Also manually ```mkdir secrete``` under / and put the file flag.txt inside the created folder

## Some notes to the CTF attacker
1. The attacker should know the basic structure of the VLAN
2. The attacker should know that the goal is to get files from a webserver running on this machine
3. The attacker should know that the range of IP relavant to the CTF is 192.168.25.*
