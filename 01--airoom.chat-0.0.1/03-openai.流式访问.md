使用 [openai 库](https://github.com/openai/openai-node)

## 流式访问

初步尝试下面的代码：

```
    import OpenAI from 'openai';

    const openai = new OpenAI({
      apiKey: process.env.OPENAI_API_KEY,
    });

    const chatStream = await openai.chat.completions.create({
        messages: [{ role: "user", content: "Say this is a test" }],
        model: "gpt-3.5-turbo",
        stream: true,
    });

    for await (const part of chatStream) {
      console.log(part);
    }
```

结果：

```
...
{
  id: 'chatcmpl-8AajPdk09lI3csITwEhZKTzc43Rsa',
  object: 'chat.completion.chunk',
  created: 1697535167,
  model: 'gpt-3.5-turbo-0613',
  choices: [ { index: 0, delta: [Object], finish_reason: null } ]
}
{
  id: 'chatcmpl-8AajPdk09lI3csITwEhZKTzc43Rsa',
  object: 'chat.completion.chunk',
  created: 1697535167,
  model: 'gpt-3.5-turbo-0613',
  choices: [ { index: 0, delta: {}, finish_reason: 'stop' } ]
}
```

