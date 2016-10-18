# socket.io Example App
This repo shows an example Socket.IO application. Users
click on two boxes to vote for "left" or "right." If you
open multiple tabs or visit the same page from multiple
computers you'll see votes automatically updated quickly.

The example app also includes a tiny chatroom where users
can post chat messages, anonomously.

## Server Basics

* Have `io` listen for `connection` events to receive sockets.
* Have each socket listen to your own custom events.

```
var http = require('http').Server(app);
var io = require('socket.io')(http);

io.on('connection', function(socket) {
  // listen for a custom event
  socket.on('player-ready', function() {
    if (allPlayersReady) {
      // broadcast custom 'start-game'
      io.emit('start-game', {info: gameInfo});
    }
  });
);
```

## Client Basics
* Create a `socket` from instantiating `io()`.
* Listen for custom events with `socket.on('str', func)`
* 

```
var socket = io();
socket.on('start-game', function() {
  // 
});

// Listen for click events with jQuery (as usual)
$('#ready-button').on('click', function() {
  // emit custom events using the socket.
  socket.emit('player-ready')
});
```

## Licensing
All content is licensed under a CC­BY­NC­SA 4.0 license.
All software code is licensed under GNU GPLv3. For commercial use or alternative licensing, please contact legal@ga.co.
