# WebSocket支持
> React Native还支持WebSocket,这种协议可以在单个TCP连接上提供全双工的通信信道。   

```
    var ws = new WebSocket('ws://host.com/path');
    ws.open = () =>{
        // 打开一个连接
        ws.send('something');//发送一个消息
    };
    ws.onmessage = (e) =>{
        //接收到了一个消息
        console.log(e.data);
    };
    ws.onerror = (e) =>{
        // 发生了一个错误
        console.log(e.message);
    };
    ws.onclose = (e) =>{
        // 连接被关闭了
        console.log(e.code,e.reason);
    };
```
