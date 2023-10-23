
Sidebar 必须要有，无论是桌面还是手机端，用于呈现房间详细信息。


[DaisyUI Drawer](https://daisyui.com/components/drawer/)很适合做 siderbar

sidebar 在右边：

```
<div class="drawer drawer-end">
  <input id="my-drawer-4" type="checkbox" class="drawer-toggle" />
  <div class="drawer-content">
    <!-- Page content here -->
    <label for="my-drawer-4" class="drawer-button btn btn-primary">Open drawer</label>
  </div>
  <div class="drawer-side">
    <label for="my-drawer-4" aria-label="close sidebar" class="drawer-overlay"></label>
    <ul class="menu p-4 w-80 min-h-full bg-base-200 text-base-content">
      <!-- Sidebar content here -->
      <li><a>Sidebar Item 1</a></li>
      <li><a>Sidebar Item 2</a></li>
    </ul>
  </div>
</div>
```

实现响应式，大屏幕时 sidebar 总是打开状态，只需要修改为：


    <div class="drawer drawer-end lg:drawer-open">

在大屏幕下，sidebar 高度超过了窗口高度，因此用 h-full 固定为视口高度：

    <div class="drawer-side h-full">

