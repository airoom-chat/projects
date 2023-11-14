每次会话开始时显示：

    --- Conversation starts ---

## 第一次访问房间

1. 首先获取当前会话数据，

2. 然后先显示：--- Conversation starts ---

3. 最后依次显示消息


## 结束会话

当会话文本长度达到阈值，结束当前会话，并显示：

    *** Conversation ends ***

### 后端

- 创建新会话，新会话状态 stat === 2
- 创建新会话第一个消息 msg


## 开始会话

当用户在一个已经结束的会话中发送消息，则新建会话，清空对话页面，重新开始会话。

### 先采用跳转的方式

后端发现当前会话 stat === 2：

- 取出第一个消息 msg
- 如果 msg 存在，则删除第一个消息，并把 msg 发送客户端

前端：

- 显示 msg
- 自动发起第一个AI消息请求


## stream with send

在消息接口，返回的是 stream，当要返回直接消息时，不是 res.write()，而是直接：

    res.status(300).send({'stat': 1, 'new_session': '............'})

在客户端仍然可以使用流解码代码，解码结果就是send完整内容，只不过是字符串格式，使用 JSON.parse 转换一下就可以。

```
                    let newData = decoder.decode(value, {stream: !done});
                    if (response.status === 300) {
                      // The session closed, goto the new session.
                      try {
                        const msg = JSON.parse(newData);
                        const new_session_uuid = msg.new_session;
                        // goto new session
                        window.location.href = `/r?uid=${user_uuid}&rid=${room_uuid}&sid=${new_session_uuid}`;
                      } catch (e) {
                        console.error('Error! JSON.parse failed: ', e);
                      }
                    }
```

### 更简单的方式

直接使用json转换即可：

```
      if (response.status === 300) {
        // The session closed, goto the new session.
        try {
          const sendInfo = await response.json();
          const sid = sendInfo.new_session;
          window.location.href = `/r?uid=${user_uuid}&rid=${room_uuid}&sid=${sid}`;
        } catch (e) {
          console.error('Error! JSON.parse failed: ', e);
        }
      }
```


## 测试1：手动修改 stat: 0 -> 1

done.

会话状态从开放（0）改为关闭（1），因为要批量将目前的会话全部关闭。另外更常见的是，用户浏览一个已经关闭的会话，再次发送信息。

当用户发送消息，后端检测到 stat == 1，则：

- 创建新会话，stat = 2
- 创建新消息
- 返回300，已经新的会话 uuid


## 测试2：访问 stat==2 的会话

done.

会话长度到达阈值之后，继续的消息将跳转到新的会话，此时新会话的 stat == 2.

- 删除消息
- 修改会话状态 stat 2 -> 0

说明：测试1和测试2可以反复测试，数据闭环，只涉及后端。


## 测试3：新会话显示用户消息，并发送

跳转新会话，这时收到的会话信息包括：

    session_stat: 2

说明用户已经发送了消息，因此显示用户消息，并发送到服务器，继续对话。


## 测试4：已关闭会话显示 *** Conversation ends ***

访问某个已经关闭的会话，显示全部消息后，最后显示：

    *** Conversation ends ***


## 测试5：每个AI回复之后，请求查看本次会话是否结束


## 测试6：线上走通




