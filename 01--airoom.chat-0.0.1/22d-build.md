
build 之后，竟然没有产生子目录：

    home/index.html
    r/index.html

而是生成这样：

    home.html
    r.html

目前的暂时解决办法：

    mkdir home
    mkdir r
    mv -i home.html home/index.html
    mv -i r.html r/index.html
    cp -ir _app home
    cp -ir _app r
    cp -ir images home
    cp -ir images r

# 最终解决办法

Nginx：

```
server {
    listen 80;
    server_name example.com;

    root /path/to/your/website;

    location / {
        index index.html;
        try_files $uri $uri.html $uri/ =404;
    }
}
```

这是 ChatGPT 给出的答案，并且解释：

In this configuration, the root directive specifies the root directory of your website. The location block handles all requests and sets "index.html" as the default index file. The try_files directive checks if the requested file exists, and if not, tries appending ".html" to the URI. If an exact match is found, it serves the file. If no match is found, it returns a 404 error.


最后，去掉路径后缀斜杠：

    rewrite ^/(.*)/$ /$1 permanent;



