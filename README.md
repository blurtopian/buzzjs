# Buzz.js

A lightweight JavaScript library for Buzz

### Install
```
npm install buzzjs --save
```

### Usage
```js
var buzz = require('buzz');

// Init WebSocket client
var client = new buzz.Client('wss://notifications.blurt.world');

// Get accounts
client.call('get_notifications', ['ericet'], function(err, result) {
  console.log(err, result);
});
```

### Promises

You can also use Buzz.js with promises by promisifying buzz with
[bluebird](https://github.com/petkaantonov/bluebird) as in:

```js
var buzz = require('buzzjs');
bluebird.promisifyAll(buzz.Client.prototype);
```

It'll add a *Async* to all buzz functions (e.g. return client.callAsync().then())

```js
// So instead of writing client.request('get_notifications', ['ericet'], cb); you have to write:
return client.callAsync('get_notifications', ['ericet']).then(function(result) {
  console.log(result); // => [{ id: 26921, name: 'fabien' ...]
});
```

## License

[MIT](LICENSE).
