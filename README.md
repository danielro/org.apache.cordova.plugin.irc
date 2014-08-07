org.apache.cordova.plugin.irc
===========
This is a simple IRC plugin for Corodova/PhoneGap on Android. Forked from https://github.com/ograycode/Cordova-IRC to be installable from CLI and compatible with *Cordova 3.0*.

## Installation

    cordova plugin add https://github.com/alexandrelaplante/org.apache.cordova.plugin.irc.git

## Limitations

This plugin is very limited in what it can do. It can only connect to one channel on one server, and can only send and receive messages.

## Usage

This plugin provides two methods, `window.plugins.irc.connect` and `window.plugins.irc.send`.

#### window.plugins.irc.connect

This method takes a callback function, to be called whenever a message a received, and the connection parameters.

```javascript
var args = [{
    username : "testuser123",
    password : "",
    channel : "#android",
    server : "irc.freenode.net",
    port : "6667",
}];

window.plugins.irc.connect(callback, args);

function callback (response) {
    var channel  = response.channel;
    var login    = response.login;
    var hostname = response.hostname;
    var sender   = response.sender;
    var message  = response.message;

    $('#irc').append('<br/>'+sender+': '+message);
}
```


#### window.plugins.irc.send

This method sends a message to the channel to which we are connected.
```javascript
var message = $('#message').val();
window.plugins.irc.send([{'contents' : message}]);
```