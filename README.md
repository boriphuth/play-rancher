# play-rancher

https://www.linuxsysadmins.com/install-docker-on-rhel-and-centos-linux/
# Installing Docker on Red Hat Enterprise Linux and CentOS Linux 7
```bash
# Step 1: Resolve Dependencies for Docker Container
$ yum install -y yum-utils device-mapper-persistent-data lvm2

# Step 2: Enable repositories for Docker Container
$ cd /etc/yum.repos.d/; curl -O https://download.docker.com/linux/centos/docker-ce.repo

# Step 3: Install Docker Package
$ yum repolist
$ yum install docker-ce docker-ce-cli containerd.io -y

# Step 4: Start and enable the service persistently
$ sudo systemctl start docker
$ sudo systemctl enable docker

# Step 5: Grant non-root user to run privileged commands.
$ sudo usermod -aG docker m6080042

# Step 6: Run a few basic commands
$ docker -v
$ docker info

```

https://www.linuxsysadmins.com/setup-kubernetes-cluster-with-rancher
```bash
# Operating System and Docker Setup
$ cat /etc/redhat-release
$ docker -v

# Start with Setting up
$ sudo docker run --name Rancher_K8s -d --restart=unless-stopped -p 80:80 -p 443:443 rancher/rancher
$ docker ps -a

docker run -d --restart=unless-stopped \
-p 80:80 -p 443:443 \
-e HTTP_PROXY="http://webproxy.pln.corp.services:80" \
-e HTTPS_PROXY="http://webproxy.pln.corp.services:80" \
-e NO_PROXY="localhost,127.0.0.1,0.0.0.0,192.168.10.0/24,10.*" \
rancher/rancher:latest

```
https://gist.github.com/superseb/2cf186726807a012af59a027cb41270d
https://stackoverflow.com/questions/48290551/how-to-fix-openshift-pod-start-failed-with-nodeunderdiskpressure

$ curl https://gist.githubusercontent.com/superseb/2cf186726807a012af59a027cb41270d/raw/eaa2d235e7693c2d1c5a2a916349410274bb95a9/cleanup.sh > ./cleanup.sh && chmod a+x ./cleanup.sh && sudo ./cleanup.sh

$ sudo systemctl stop docker && sudo rm -rf /var/lib/docker && sudo systemctl start docker && sudo systemctl status docker
$ docker rm -vf $(docker ps -a -q) && docker rmi -f $(docker images -a -q)