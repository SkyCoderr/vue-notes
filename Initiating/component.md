# Initiating a component

## Example
```javascript
Vue.component('componentName', {options})
```
```javascript
Vue.component('componentName', {
    props: {
        message: {
            type: String,
            required: true,
            default: 'Default Message'
        }
    },
    template: `<h1>{{ message }}</h1>`,
    data() {
        return {
            ...
        }
    }
})
```

`componentName` is the name of the component being created. `options` is nearly identical to the options object in the Vue instance.

## options

### template
* Instead of plugging into an element in the DOM like in the Vue instance, a component has a template property, which specifies the structure of the component.
* Component template can only return one root element. If there's multiple, try to wrap them into one single element.

### data
* The `data` in components is a **function** that returns a data object (So that if the component is used throughout the app, each copy of the component will have their own data object, instead of sharing one `data` object).

### props
* The `props` option is an array of attributes that the component expects to receive from the parent.
* It is recommended to use a props object instead of a props array. So that we can specify the data type of each prop, and whether it is required, even its default.

### mounted
* `mounted` is a lifecycle hook.
* A place to put the code as soon as the component is mounted to the DOM