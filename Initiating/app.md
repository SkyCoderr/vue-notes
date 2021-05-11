# Initiating an app

## Example
```javascript
var app = new Vue(options);
```
```javascript
var app = new Vue({
    el: '#app',
    data: {
        ...
    },
    methods: {
        ...
    },
    computed: {

    },
    ...
})
```

`options` is an object that contains parameters like `data` and `methods` to initiate the vue object

## Parameters in `options`
  
### el
* The value of `el` (not `element`) specifies the name of the app that will be referenced in DOM.
* The value of `el` is a string, and contains a `#` at the beginning, e.g. `'#app'`.

### data
* An object that accommodates all the data used by this vue instance.
* Variables in `data` can be directly accessed in DOM. They can also be accessed within the vue instance using the keywork `this`, e.g. `this.productName`.

## Emits
```javascript
this.$emit('event-name', parameter1, parameter2, ...)
```
```html
<component @event-name="parentMethod"></component>
```
* Components can't modify variables in their parents, so in order to communicate backwards, we use emits. 
* The first argument in `$emit` function is the name of the event, and it has to be in quotes, followed by a list of parameters to be passed back to the parent together.
* The parent should have an event listener on the component `@event-name`, and triggers a function call in the parent when this event happens.
* The same list of parameters from the emit is passed into `parentMethod`.