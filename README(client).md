# README file for the client
## How to run the client
1. Create a sandbox and a folder called client inside the sandbox
2. Migrate into the client folder and put the Dockerfile.client inside it
3. Build and run the docker
```
docker build -t client .
docker run -d --name client --dns 192.168.25.10 --dns-search netsec-docker.isi.jhu.edu --privileged --ip 192.168.25.157 --cpus=1 tclient:latest
docker exec -it client bash
```
