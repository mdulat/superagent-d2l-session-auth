# superagent-d2l-session-auth

[![NPM version][npm-image]][npm-url]
[![Build status][ci-image]][ci-url]
[![Coverage Status][coverage-image]][coverage-url]

A superagent plugin that adds D2L auth headers

## Usage

```js
var request = require('superagent'),
    auth = require('superagent-d2l-session-auth');

request
    .get('/d2l/api/lp/1.5/users/whoami')
    .use(auth())
    .end(function(err, res) {
        if(err) {
           console.log('I always check for errors! ' + err.status + ' ' + err.response);
           return;
        }
        var user = res.body;
        console.log('Hello, ' + user.FirstName + ' ' + user.LastName);
    });
```


### API

---

#### `auth([Object options])` -> `Function`

The export is a factory function which creates the superagent plugin. The
result of this call is what should be passed into `.use`.

##### Option: trustedHost `String`

You may optionally specify an additional host which is trusted and which
authorization tokens should be sent to. This should be generally unnecessary,
and should only be an instance of Brightspace.

```js
request
	.get('https://school.brightspace.com/api')
	.use(auth({
		trustedHost: 'school.brightspace.com'
	}))
	.end(/* ... */);
```


[npm-url]: https://npmjs.org/package/superagent-d2l-session-auth
[npm-image]: https://badge.fury.io/js/superagent-d2l-session-auth.png
[ci-image]: https://travis-ci.org/Brightspace/superagent-d2l-session-auth.svg?branch=master
[ci-url]: https://travis-ci.org/Brightspace/superagent-d2l-session-auth
[coverage-image]: https://img.shields.io/coveralls/Brightspace/superagent-d2l-session-auth.svg
[coverage-url]: https://coveralls.io/r/Brightspace/superagent-d2l-session-auth?branch=master
