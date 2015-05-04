
Conexión a sockets con namespace y rooms
----------------------------------------

```
var customNS = ioserver.of('/chat'); 

customNS.on('connection', function (socket) {
   socket.on('message', function (msg) {

       // Send message to sender 
       socket.emit(msg);

       // Send message to everyone on customNS INCLUDING sender
       customNS.emit(msg);

       // Send message to everyone on customNS BUT sender
       socket.broadcast.emit(msg);

       // Send message to everyone on ROOM chanel of customNS INCLUDING sender
       customNS.in('ROOM').emit(msg); 

       // Send message to everyone on ROOM chanel of customNS BUT sender
       socket.broadcast.in('ROOM').emit(msg); 


   });
});
```
