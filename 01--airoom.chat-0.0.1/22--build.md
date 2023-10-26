
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


