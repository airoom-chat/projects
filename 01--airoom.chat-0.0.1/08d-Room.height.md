Room height is the same of viewport height.


# 带滚动条的对话框

要显示垂直滚动条，css：

    overflow-y: auto;

TW:

    .overflow-y-auto

并且，还要有 height 值！


# 计算 height

在页面加载时，以及窗口大小变化时（resize事件），计算消息框高度，并设置高度：

```
  import { onMount } from 'svelte';
  onMount(() => {
    const setHeight = () => {
      const chatBoxHeight = window.innerHeight - 66 - 60 - 23;
      const msgbox = document.getElementById('msgbox');
      if (msgbox) {
        msgbox.style.height = `${chatBoxHeight}px`;
      }
    }

    setHeight();

    addEventListener('resize', (evt) => {
      setHeight();
    })
  })
```

