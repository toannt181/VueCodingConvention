# Vuejs Coding Style Guide

[![js-standard-style](https://cdn.rawgit.com/standard/standard/master/badge.svg)](https://github.com/standard/standard)
<img src="https://vuejs.org/images/logo.png" height="60" width="60" />

This is summary of best practicals based on [standard](https://github.com/standard/standard) JavaScript
rules and [Vuejs style guide](https://vuejs.org/v2/style-guide/)

There are some adjustments for enhancing the readability of code and make us feel more comfortable when following this style guide.

StyleGuide is divided by 3 parts
- Strict Rules: You should strictly follow this convention. There are not only the standard coding style guide javascript in general but also is completed instruction. This part also improves lots of quality codes.
- Checklist: It's compulsory, is the checklist for the most common situations you may meet when developing, follow this part to make sure that your code is lint, clean and clear. I also add some practicals for checklist help you can truthy understand it.
- Practicals: The best real practicals and described the main point, you'd better notice.

## Rules
* **Follow standard javascript rule**:
https://github.com/feross/standard/blob/master/RULES.md#javascript-standard-style <br>
You can also choose Airbnb Convention here https://github.com/airbnb/javascript It's great and described very clearly.
* **Follow Essential and Strongly Recommended in StyleGuide Vuejs**: https://vuejs.org/v2/style-guide/

## Checklist
- **Self-checking before creating pull request**
  - [ ] **The code runs**, no errors throw
  - [ ] Check branch name and commit
  - [ ] Eslint and unit test has no error `npm run lint` `npm run test`
  - [ ] Code follows these upper conventions
  - [ ] Prechecking layout with tools (ex. Perfect pixel extension)
  - [ ] Prechecking in crossing browsers (IE10, IE11, Edge, Safari, ...)
- **Reviewing code**
  - Markup
    - [ ] Self close tag if possible
    - [ ] Shouldn't use one word for naming component for preventing collapsing html tag
    - [ ] The maximum length code in one file should be < 120
    - [ ] Number of attribute not exceed 4 in oneline (best for reading)
  - Javascript
    - [ ] Name vars and function are meaning, short, simple and spelt correctly
    - [ ] Use Containers and Components concept to handle logic code
    - [ ] Boolean vars should start with is/has/should
    - [ ] There are no usages of 'magic numbers', use constants instead
    - [ ] Comments are optional
    - [ ] Code is not repeated or duplicated. Consider using utilize methods, mixins, HOC instead
    - [ ] Using return for get away of else case
    - [ ] No empty block of code
    - [ ] The number of parameters of function if has more than 3 should be declare as object destructuring
    - [ ] Function return same type of output
    - [ ] Immutable vars should declare in created method, construction method instead of in data declaration method
    - [ ] Number of lines of one file not exceed 150 (for file contain js only), 300 (for containing both html css and js)
    - [ ] No semi colons for cleaning code (javascript is good at handling it)
    - [ ] No nested ternary operator (For better readable)

## Practicals
* **Indention in .vue file**
  - No indent first line (except in html)
  - One break line after each tag
  - Prefer using pug instead pure html
  - Bad:
  ```html
  <template>
  <button
    class="btn"
    :disabled="disabled || loading"
    @click="$emit('click')"
  >
    <div v-if="loading" class="loading" /><slot />
  </button>
  </template>

  <script>
    export default {
      name: 'Button',
      data: function() {
        return { value: 1 }
      }
    }
  </script>
  <style lang="scss" scoped>
    .btn {
      &--blue {
        color: blue;
      }
        &--green {
          color: blue;
        }
    }
  </style>
  ```
  - Good
  ```html
  <template>
    <button
      class="btn"
      :disabled="disabled || loading"
      @click="$emit('click')"
    >
      <div v-if="loading" class="loading" />
      <slot />
    </button>
  </template>

  // or in pug template

  <template lang="pug">
  button.btn(:disabled="disabled || loading" @click="$emit('click')")
    div.loading(v-if="loading")
    slot
  </template>

  <script>
  export default {
    name: 'Button',
    props: {
      disabled: {
        type: Boolean,
        default: false,
      },
      loading: {
        type: Boolean,
        default: false,
      },
    },
  }
  </script>

  <style lang="scss" scoped>
  .btn {
    &--blue {
      color: blue;
    }
    &--green {
      color: blue;
    }
  }
  </style>
  ```

* **Directive shorthands**
  - Directive shorthands (: for v-bind: and @ for v-on:) should be used always or never.
  - Bad
  ```js
  <input
    v-bind:value="newTodoText"
    :placeholder="newTodoInstructions"
  >
  ```
  - Good
  ```js
  <input
    :value="newTodoText"
    :placeholder="newTodoInstructions"
    @focus="$emit('focus')"
  >
  ```

* **Function key ES6**
  - Use shorthand writing funtion as key in Object
  - Bad
  ```js
  data: function() {
    ...
  }
  ```
  - Bad
  ```js
  data: () => {
    ...
  }
  ```
  - Good
  ```js
  data() {
    ...
  },
  methods: {
    test() {
    ...
    }
  }
  ```

* **Don't use this in template**
  - Use `this` is unnecessarily in the template tag
  - Bad
  ```js
    <button @click="this.next()">Click me</button>
  ```
  - Good
  ```js
    <button @click="next">Click me</button>
  ```

* **Always trailing commas**
  - Get away of git conflict
  - Bad
  ```js
    const person = {
      name: 'Toan',
      age: 100
    }
  ```
  - Good
  ```js
    const person = {
      name: 'Toan',
      age: {
        type: Number,
        default: 1000,
      },
    }
  ```

* **Using return for get away of else case**
  - Bad
  ```js
    if (isLoading) {
      this.text = 'loading'
    } else {
      handleThing()
    }
  ```
  ```js
    if (isDone) {
      handleThingA()
      if (isSended) {
        handleThingB()
      }
    }
  ```
  - Good
  ```js
    if (isLoading) {
      this.text = 'loading'
      return
    }
    handleThing()
  ```
  ```js
    if (!isDone) return
    handleThingA()
    if (isSended) {
      handleThingB()
    }
  ```
## **Reference**
  - https://github.com/feross/standard/blob/master/RULES.md#javascript-standard-style 
  - https://github.com/airbnb/javascript 
  - https://vuejs.org/v2/style-guide/