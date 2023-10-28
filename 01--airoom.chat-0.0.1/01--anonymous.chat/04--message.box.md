组件：

    RoomMessageTextarea.svelte

发送消息输入框包括：

- textarea
- "Send" button

使用 Enter 作为消息发送，这样很方便。


## Send message

绑定 keydown 事件：

    on:keydown={handleKeydown}


