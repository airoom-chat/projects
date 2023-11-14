
footer通常写版权信息等，显示在页面底部。如果页面内容过少，则footer会出现在屏幕中间位置，很尴尬。在 Tailwind 中，你可以使用flex来实现footer保持在屏幕或页面底部。

代码：

```
<div class="flex flex-col min-h-screen">
  <slot />

  <footer class="footer footer-center p-4 bg-base-300 text-base-content mt-auto">
    <aside>
      <p>Copyright © 2023 - All right reserved by airoom.chat</p>
    </aside>
  </footer>
</div>
```
用flex包裹全部页面内容，footer设置类名：mt-auto 即可。

参考：[playground](https://play.tailwindcss.com/WVAkB96r6Y)


