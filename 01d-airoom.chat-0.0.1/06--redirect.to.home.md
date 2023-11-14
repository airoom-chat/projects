todo: / 和 /home 页面一样，因为现在只有非注册用户！


# 逻辑

网站首页，包括 Hero 部分：

    https://airoom.chat/home

登陆用户则停留在 / 首页，没有 Hero 部分：

    https://airoom.chat


# load

Svelte 页面在加载时，会执行 load() 函数，只要这个函数在 +page.js 中进行了定义。下面是实现的代码：

```
import { redirect } from '@sveltejs/kit';
import { browser } from '$app/environment';

export function load({ params }) {
  if (browser) {
    const access_token = localStorage.getItem('access_token');
    if (!access_token || !access_token.length || access_token.length < 15) {
      throw redirect(302, '/home');
    }
  }
 }

```

这个实现还有一点问题，就是 / 页面会闪现！因此，最好的解决办法是和 github 一样：

    对于非登录用户，/ 和 /home 内容一样；
    对于登录用户，/ 作为自己的客户化首页。


# 错误尝试

代码：

```
  // Redirect to home if not logged in
  import { onMount } from 'svelte';
  import { goto } from '$app/navigation';

  onMount(() => {
    const access_token = localStorage.getItem('access_token');
    if (!access_token || !access_token.length || access_token.length < 15) {
      goto('/home');
    }
  })
```

上面这个方法，导致浏览器返回键失效！点击返回键仍然回到 /home 页面！

但是使用 302 跳转则没有这个问题。


