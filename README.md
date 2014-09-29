eventful-node
=============

A simple client library for the Eventful API for event searching. (http://api.eventful.com)

# Getting Started

(In the near future you will be able to) Do:

```bash

npm install eventful-node

```

Then you can require and intiailze a new client with your api_key:

```js

var eventful = require('eventful-node');
var client = new eventful.Client(<YOUR EVENTFUL API KEY>);

```

## Searching for events

To search you can use the search function. Pass a [searchEventOptions](https://github.com/sedouard/eventful-node/blob/master/lib/eventful-node.d.ts) and the [callback](https://github.com/sedouard/eventful-node/blob/master/lib/eventful-node.d.ts).

```js

client.searchEvents({ options }, callback);

```

Example - Get all events listed in eventful with keyword 'music':

```js

client.searchEvents({ keywords: 'music' }, function(err, data){

  if(err){
  
    return console.error(err);
  
  }
  
  console.log('Recieved ' + data.total_items + ' events');
  
  console.log('Event listings: ');
  
  //print the title of each event
  for(var i in data.events){
  
    console.log(data.events[i].title);
  
  }

});

```

# Building

This library is built and tested using [gruntjs](http://gruntjs.com). Be sure to have the grunt command line interface (cli) installed globally on your machine:

```bash
npm install grunt-cli -g
```

To build eventful-node, fork or clone this repository and do:

```bash

npm install --dev
grunt

```

This will compile the [typescript](http://typescriptlang.org) into javascript, minify it and place it in the ./lib folder.

# Testing

To run the associated unit tests do:

```bash
grunt test
```

# Contributing

This library is written in [typescript](http://typescriptlang.org) and as such contributions must be made in typescript. To make things easier, you can start this grunt watch task which will automatically validate and compile your typescript into javascript.

Please check the issues tab with 'help wanted' issues to contribute.

```bash
grunt watch
```
