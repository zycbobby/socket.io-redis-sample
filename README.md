# Learning Note
Key code:


```javascript
var io = require('socket.io')(server);
var redis = require('socket.io-redis');
io.adapter(redis({ host: '127.0.0.1', port: 6379 }));

io.sockets.on('connection', function(socket) {
  socket.on('message', function(data) {
    socket.broadcast.emit('message', data);
  });
  socket.on('redis', function(data) {
      console.log('receive from redis :' + data);
  });
});
```
broadcast 和 emit都不仅仅能找到当前进程所handle的sockets,而且能找到redis里头存的sockets，并且广播或者定向发送


# socket.io-redis-sample

This is simple node.js application with [Express.js 4.x](https://github.com/visionmedia/express), [Socket.IO 1.x](https://github.com/automattic/socket.io) and [socket.io-redis](https://github.com/Automattic/socket.io-redis).

## Usage

```
$ redis-server &
$ git clone https://github.com/stoshiya/socket.io-redis-sample.git
$ cd socket.io-redis-sample
$ npm install
$ PORT=3000 node app.js &
$ PORT=3001 node app.js &
```

## License

MIT
