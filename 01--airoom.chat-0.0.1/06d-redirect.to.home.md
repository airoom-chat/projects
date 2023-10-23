
## 网站主页

网站首页，包括 Hero 部分：

    https://airoom.chat/home

登陆用户则停留在 / 首页，没有 Hero 部分：

    https://airoom.chat

Svelte 页面在加载时，会执行 load() 函数，只要这个函数在 +page.js 中进行了定义：


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




