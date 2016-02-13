# super-event-emitter

[![npm version](https://badge.fury.io/js/super-event-emitter.svg)](https://badge.fury.io/js/super-event-emitter)

> Super small and simple interpretation of popular event management.

I was create blog post (in polish language) about this tool: http://piecioshka.pl/blog/2016/01/29/super-event-emitter.html

## Install

```
npm install super-event-emitter
```

## Usage

Simple literal object:

```javascript
var foo = EventEmitter.mixin({});
foo.on('test', function () {
    console.log('triggered!');
}, this);
foo.emit('test');
```

Existed object: 

```javascript
var bar = {}; // Or any other object.
EventEmitter.mixin(bar);
bar.on('test', function () {
    console.log('triggered!');
}, this);
bar.emit('test');
```

## API

#### `on( name, fn, ctx )`

 * `name` - a string value representing the name of event
 * `fn` - action which will be called when event will be triggered
 * `ctx` - object will be context of triggered action

Example usage:

```javascript
instance.on('foo', function (data) {
    console.log(data, this);
}, instance);
```

#### `once( name, fn, ctx )` - The same as `on` but, after triggered event, destroy all listeners

Example usage:

```javascript
instance.once('foo', function (data) {
    console.log(data, this);
}, instance);
```

#### `off( name, fn )`

 * `name` - a string value representing the name of event
 * `fn` - action which will be removed from listeners
 
Example usage:

```javascript
instance.off('foo', fooHandler);
```

#### `emit( name, params )`

 * `name` - a string value representing the name of event
 * `params` - will be passed as first argument in called actions

Example usage:

```javascript
instance.emit('foo', { name: 'bar' });
```

---

In some reasons (compatibility with any other APIs) I add some **aliases**:
 
 * `on` => `addEventListener`, `addListener`
 * `off` => `removeEventListener`, `removeListener`
 * `emit` => `trigger`

## Unit test

How to run unit test (written in Jasmine):

```
npm test
```

## License

[The MIT License](http://piecioshka.mit-license.org) @ 2016
