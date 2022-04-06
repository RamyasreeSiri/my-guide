# VUE

## VUE-3 Frontend Masters - Sarah Darsner

[course 1 Introduction to Vue3 repo](https://github.com/sdras/intro-to-vue)

[course 2 repo](https://github.com/sdras/building-web-apps-with-vue)

[course pdf](https://static.frontendmasters.com/resources/2020-09-25-building-apps-vue/building-vue-apps-1.pdf)


## Why?

- Declarative
    <details>
    <summary>Declarative programming vs. imperative programming</summary>

    ---
    Declarative programming relies on underlying components of a given language
    to carry out the necessary steps to reach the stated outcome.

    In declarative programming,
    typical programming constructs such as loops and if/then conditions do not exist,
    because they are instructional.

    Declarative programming focuses on the end result,
    while imperative programming focuses on how to get there.

    For example, when you jump in a taxi,
    you declare to the driver where you want to go.

    You don't tell him how to get there by providing turn-by-turn directions.
    The turn-by-turn directions are akin to imperative programming.

    Declarative programming builds on the capabilities developed by imperative programming,
    but enables the developer to focus on problem resolution rather than
    intricacies of code setup.
    </details>
    <br />
- Legible(clear enough to read)

- Easy to Maintain

- Powerful

- A collection of the best of the best

- Elegant

- Gives me what I want when I need it, and gets out of my way

- A way to be really productive

## COMPARISON WITH OTHER FRAMEOWRKDS

- A virtual DOM
- Reactive components that offer the View layer only

- Props and a centralized stage management store similar to React.

- Conditional rendering, and services, similar to Angular.

- Inspired by Polymner for simplicity and performance,
    Vue offers a similar development style as HTML,
    styles and JavaScript are composed in tandem.

- Scoped tyles in SFC that are similar to some types of CSS-in-JS like CSS Modules.

## Directives

- v-text
- v-html
- v-show

    <details>
    <summary>Definition</summary>

    ---
     Toggles the element's display CSS property based on the truthy-ness
     of the expression value.

      This directive triggers transitions when its condition changes.

    [Refer Documentaion](https://v3.vuejs.org/guide/conditional.html#v-show)
    </details>

- v-if

    <details>
    <summary>Definition</summary>

    ---
    Is a conditional that will display information depending on meeting a requirement.
    This can be anything - buttons, forms, divs, components

    The element and its contained directives / components are
    destroyed and re-constructed during toggles.

    When used together, v-if has a higher priority than v-for.
    We don't recommend using these two directives together on one element

    [Refer Documentation](https://v3.vuejs.org/guide/conditional.html#v-if)
    </details>
    <br />
- v-else
    <details>
    <summary>Definition</summary>

    ---
    Denote the "else block" for v-if or a v-if/v-else-if chain.
    </details>
    <br />
- v-else-if
- v-for
- v-on
- v-bind
- v-model

    <details>
    <summary>Definition</summary>

    ---
    Creates a relationship between the data in the instance/component and a form
    input, so you can dynamically update values
    [Refer Documentation](https://v3.vuejs.org/guide/forms.html#basic-usage)
    </details>
    <br />
- v-slot
- v-pre
- v-cloak
- v-once
- v-memo
- v-is

[v-if vs v-show](https://v3.vuejs.org/guide/conditional.html#v-if-vs-v-show)

[v-if with v-for](https://v3.vuejs.org/guide/conditional.html#v-if-with-v-for)

## Creating and Mounting an app

```js

Vue
.createApp({
    data: function() { 
        return {
            value: value1
        }
    },
    methods: {
        method: function method1() {}
    },
    computed: {
        computed: function computedValue1() { return value; }
    }
})
.mount('#id');

```
[Reference: https://www.vuemastery.com/courses/intro-to-vue-3/intro-to-vue3/](https://www.vuemastery.com/courses/intro-to-vue-3/intro-to-vue3/)
[Repo: note-vuemastery-intro-to-vue-3](https://github.com/RamyasreeSiri/note-vuemastery-intro-to-vue-3)
## Attribute Binding

```html
<!-- shorthand of v-bind -->
<img :src="image">

<img v-bind:src="image">
```

[Reference: Course referred by Vue documentation](https://www.vuemastery.com/courses/intro-to-vue-3/attribute-binding-vue3)

## Conditional Rendering

```html

<p v-if="onSale">on Sale</p>
<p v-else>Sale Ended</p>
```

## List Rendering

```html

<div v-for="variant in variants" :key="variant.id">
    {{ variant.color }}
</div>
```

## Event handling

```html

<button class="button" v-on:click="addToCart">Add to Cart</button>

<!-- shorthand of v-on -->
<button class="button" @click="addToCart">Add to Cart</button>
```

## Class and Style binding

```html
<!-- style binding -->
<div v-for="variant in variants" :key="variant.id" @mouseover="updateImage(variant.image)" class="color-circle" :style="{ backgroundColor: variant.color}">

<!-- class binding -->
<img :src="image" :class="[inventory == 0 ? 'out-of-stock-img' : '']" />

<button class="button" :class="{ disabledButton: inventory < 1}" @click="addToCart" :disabled="inventory < 1">Add to Cart</button>
```

## Computed Properties

- these functions memoize the values

```html
<!-- html -->
 <h1>{{ title }}</h1>

<!-- js -->
  computed: {
    title() {
      return this.brand + ' ' + this.product;
    }
  }
```

## Components and Props

**Component**: Building blocks of Vue app

```js

app.component('product-details', {
  props: {
    details: {
      type: Array,
      required: true
    }
  },
  template:
  /*html*/
  `<ul>
    <li v-for="detail in details">{{ detail }}</li>
  </ul>`
})
```

**Props**: A custom attribute for passing data into a component

```js

<product-details :details="details"></product-details>
```

## Communicating Events

**Emitting Events**: Tell *Parent* when event happens

```js

// listening to event
<product-display :cart="cart" @add-to-cart="updateCart"></product-display>

// emitting event
methods: {
    addToCart() {
        this.$emit('add-to-cart');
    }
}
```

## Forms

**v-modal** is used in forms as two-way binding of data is done,
as user updated the input, the name in our data funciton will be updated

```html

`<form class="review-form" @submit.prevent="onSubmit">
<h3>Leave a review</h3>
<label for="name">Name:</label>
<input id="name" v-model="name">`

<!-- v-model does two way binding -->
data() {
    return {
      name: ''
    }
}
```
