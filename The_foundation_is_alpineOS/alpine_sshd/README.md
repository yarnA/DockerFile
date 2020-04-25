## 构建使用指南

```bash
#Perform the following operations to build the image
git clone https://github.com/yarnA/DockerFile.git
cd  DockerFile/The_foundation_is_alpineOS/alpine_sshd
docker build -t  alpine_sshd:latest  .

docker run -itd -p 60022:22 alpine_sshd
#Now you can run the command "ssh -p 60022 root@localhost"  to connect to the container
```
