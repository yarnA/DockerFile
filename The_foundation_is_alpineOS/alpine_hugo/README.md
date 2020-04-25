## 构建指导

```bash
#Perform the following operations to build the image
git clone https://github.com/yarnA/DockerFile.git
cd  DockerFile/The_foundation_is_alpineOS/alpine_hugo
docker build -t  alpine_hugo:latest  .
mkdir -p /app/YangLxy/content/post/
docker run -itd   -p 1313:1313 -v /app/YangLxy/content/post/:/app/YangLxy/content/post/ alpine_hugo:latest
#Now you can visit  http://localhost:1313   to view your blog.
```
