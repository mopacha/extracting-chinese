关于 Node.js®

作为异步驱动的 JavaScript 运行时，Node 被设计成可升级的网络应用。在下面的“Hello World”示例中，许多连接可以并行处理。每一个连接都会触发一个回调，但是如果没有可做的事情，Node 就进入睡眠状态。

const http = require('http');

const hostname = '127.0.0.1';
const port = 3000;

const server = http.createServer((req, res) => {
  res.statusCode = 200;
  res.setHeader('Content-Type', 'text/plain');
  res.end('Hello World\n');
});

server.listen(port, hostname, () => {
  console.log(`Server running at http://${hostname}:${port}/`);
});
这与今天使用 OS 线程的更常见并发模型形成了对比。基于线程的网络效率相对低下，使用起来非常困难。此外，Node 的用户不必担心死锁过程, 因为没有锁。Node 中几乎没有函数直接执行 I/O 操作，因此进程从不阻塞。由于没有任何阻塞，可伸缩系统在 Node 中开发是非常合理的。