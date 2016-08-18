# ricoh-theta npm
Node.js client for RICOH THETA - 360-degree camera

[![Build Status](https://travis-ci.org/shokai/node-ricoh-theta.svg?branch=master)](https://travis-ci.org/shokai/node-ricoh-theta)

- https://github.com/shokai/node-ricoh-theta
- https://www.npmjs.com/package/ricoh-theta


## Install

    % npm install ricoh-theta


## theta command

    # global install
    % npm install ricoh-theta coffee-script -g

    % theta --help
    % theta --capture
    % theta --capture out.jpg
    % theta --list
    % theta --id [object_handle] --save out.jpg
    % theta --volume 0


## Usage

```javascript
var fs    = require('fs');
var Theta = require('ricoh-theta');

var theta = new Theta();
theta.connect('192.168.1.1');

// capture
theta.on('connect', function(){
  theta.capture(function(err){
    if(err) return console.error(err);
    console.log('capture success');
  });
});

// get picture
theta.on('objectAdded', function(object_handle){
  theta.getPicture(object_handle, function(err, picture){
    fs.writeFile('tmp.jpg', picture, function(err){
      console.log('picture saved => tmp.jpg');
      theta.disconnect();
    });
  });
});
```

## Develop

    % npm run watch
    # or
    % npm run build

## Test

    % npm test


## Contributing

1. Fork it
2. Create your feature branch (`git checkout -b my-new-feature`)
3. Commit your changes (`git commit -am 'Add some feature'`)
4. Push to the branch (`git push origin my-new-feature`)
5. Create new Pull Request

![Analytics](https://ga-beacon.appspot.com/UA-73311422-5/Node-client)

