
弹出 sidebar 的按钮应当只在小屏幕时显示，并且只在 Room 页面显示。前者通过响应式实现，后者要通过判断当前路径是否是 /r 来实现。

在组件中，使用下面的代码来判断当前路径：

```
import { page } from '$app/stores';
  let isRoom = false;
  page.subscribe(value => {
    if (value.route.id === '/r') {
      isRoom = true;
    }
  });
```

然后，就可以在HTML中进行条件判断：

```
    {#if isRoom}
      <label for="my-drawer-4" class="drawer-button btn btn-primary" on:click={openit}>Open drawer</label>
    {/if}
```

