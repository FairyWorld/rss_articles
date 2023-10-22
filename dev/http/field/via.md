# via 字段

via 字段表示通信经过的代理服务器，多个代理服务器之间使用逗号分隔。

它用来追踪客户端与服务器之间的通信传输路径。数据经过中间服务器时，会在 Via 中附加该服务器的信息，然后再进行转发。

```http
via: proxy2, proxy1
```

上面示例表示，数据先经过 proxy1，再经过 proxy2。

Via 首部是为了追踪传输路径，所以经常会和 TRACE 方法一起使用。比如，代理服务器接收到由 TRACE 方法发送过来的请求（其中 Max-Forwards: 0）时，代理服务器就不能再转发该请求了。这种情况下，代理服务器会将自身的信息附加到 Via 首部后，返回该请求的响应。