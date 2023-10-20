------
status: done
------

## 去掉 Login

MVP 版本只支持匿名访问，不支持登录、注册。

删除如下代码：

    <div id="userinfo-wrapper" class="flex-none">
      <a href="/" class="btn btn-ghost btn-md text-lg rounded-btn normal-case
                         bg-amber-100 hover:bg-amber-300">
          Login
      </a>
    </div>

## airoom.chat 去掉 hover 背景颜色

去掉元素的背景颜色是：

    bg-transparent

因此，去掉 :hover 背景颜色（background-color）：

    hover:bg-transparent

