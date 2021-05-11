## v-bind
* Dynamically binds an attribute to an expression.
* Keeps the attribute up to date with the value of the expression.
* The example below binds the value of `expression` to the attribute `src`.  

        v-bind:src="expression"
* Shorthand for v-bind: remove `v-bind` and just keep the colon `:`.

        :src="expression"

## v-model
* `v-bind` is a one-way binding from data to template, but `v-model` is a two-way binding that keeps both of them updated with each other
 * `v-model` essentially is a `v-bin` + an `emit`.

## v-if v-else-if v-else v-show
* `v-if`, `v-else-if` and `v-else` Evaluate the expression, add the element to DOM if the expression is truthy and remove it if it's not.
* `v-show` adds the element to DOM anyways but only displays it when the expression is truthy, otherwise hides it by modifying the style of the element.
* If an element is displayed and hidden constantly, it's preferrable to use `v-show` performance-wise. Because it doesn't add and remove the element from DOM constantly, but only toggles the css attribute on and off.

## v-for
* E.g.
```html
<li v-for="variant in variants" :key="variant.variandId">{{ variant.variantName }}</li>
```
```javascript
variants: [
    {
        variantId: 1,
        variantName: "cat"
    },
    {
        variantId: 2.
        variantName: "dog"
    }
]
```
* Loops over an array of objects.
* `v-for="variant in variants"` here `variant` is an alias refering to the corresponding element in the array during each iteration.
* For arrays containing complicated objects, it's highly recommended to use the `:key` attribute, so vue can keep track of each node's identity.

## v-on
* Shorthand for `v-on` is `@`, so `v-on:click="functionName"` is equivalent to `@click="functionName"`.
* Refer to cheat sheet for a full list of events

## Style Binding
* If style is dynamic, or the value of the style attribute is a variable or contains a variable, we need to use style binding (`:sytle="{ fontSize: valueOfFontSize }"`) instead of style (`style={ fontSize: '13px' }`).
* When using kebab-case instead of camel-case for attributes in style, we need to put single quotes on the attribute names: `:style="{ 'font-size': valueOfFontSize }"`.
* It's neater to bind a style to a style object variable, we can also bind it to an array of style objects, e.g. `:style="[styleObject1, styleObject2]"`, and style property will use them both.

## Class Binding
* Like style binding, if the class of an element is dynamic, we need to use class binding.
* Inside the object to be binded to class property, the values can only be `true` or `false`. E.g. `:class="{ header: trueOrFalse, table: trueOrFalse }"`.
* Same as style binding, single quotes should be added to class names if we are using kebab-case. E.g. `:class="{ 'table-footer': trueOrFalse }"`
* We can bind a class object or an array of class objects to a class attribute.
* Conditional logics in class binding: `:class="[isHeader ? 'header' : 'table']"`, as can be seen, the conditional expression has to be in a `[]`.

## Computed Properties
* `computed` lives in a parallel level with `data` and `methods`.
* Computed variables don't take arguments.
* Whenever its dependency changes, computed properties run again and update themselves.
* The results of computed properties are cached until their dependencies change.
* It's more efficient to use a computed property rather than a method for an expensive operation that you don't want to re-run every time you access it.

## Event Bus
* An event bus is essentially a Vue instance that acts as a global channel for all components across the globe to communicate through.
```javascript
var eventBus = new Vue();
```
* For example, for a grandchild component to communicate with a grandparent:
```javascript
// instead of using:
this.$emit('event-name', payload);
// we use:
eventBus.$emit('event-name', payload);
```
* For the grandparent to listen to this event through this event bus, the grandparent would need to have a mounted property that listens to this event through this event bus.
```javascript
mounted () {
    eventBus.$on('event-name', payload => {
        // callback function code
    })
;}
```

