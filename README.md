# Vuejs Coding Style Guide

[![js-standard-style](https://cdn.rawgit.com/standard/standard/master/badge.svg)](https://github.com/standard/standard)
<img src="https://vuejs.org/images/logo.png" height="60" />

This is summary of best practicals based on [standard](https://github.com/standard/standard) JavaScript
rules and [Vuejs style guide](https://vuejs.org/v2/style-guide/)

There are some adjustment for enhancing the readability of code and make us fell more comfortable when follow this styleguide.

StyleGuide is divided by 3 parts
- Strict Rules: You should strictly follow this convention. There are not only the standard coding style guide javascipt in general but also is complete instruction. This part also improves lots of quality codes.
- Checklist: It's compulsory, is the checklist for the most common situations you may met, follow this part to make sure that your code is linted.
- Practicals: Best real practical and describe the main point need to notice.

## Rules
* **Follow standard javascript rule**:
https://github.com/feross/standard/blob/master/RULES.md#javascript-standard-style <br>
You can also choose Airbnb Convention here https://github.com/airbnb/javascript It's great and described very clear.
* **Follow Essential and Strongly Recommended in StyleGuide Vuejs**: https://vuejs.org/v2/style-guide/

## Checklist
- **Create pull request**
  - [ ] **The code runs**, no error throw
  - [ ] Check branch name and commit
  - [ ] Eslint and Unit test has no error
  - [ ] Code follows these upper conventions
  - [ ] Prechecking layout with tools (ex. Perfect pixel)
  - [ ] Prechecking in crossing browsers
- **Review code checklist**
  - Markup
    - [ ] Self close tag
    - [ ] Shouldn't use one word for naming component
    - [ ] Lines in one file should be < 150
    - [ ] Number of attribute not exceed 4 in oneline (best for reading)
  - Javascript
    - [ ] Name vars and function are meaning, short, and simple,spelt correctly
    - [ ] Use containers and Components concept to handle logic code
    - [ ] Boolean var should start with is/has/should
    - [ ] There are no usages of 'magic numbers', use constants instead
    - [ ] Comments are not nessasary
    - [ ] No console.log
    - [ ] Code is not repeated or duplicated
    - [ ] Using return for handle if else case
    - [ ] No empty blocks of code
    - [ ] The number of parameters of function if has more than 3 should be declare as object destructuring
    - [ ] Function return same kind of output
    - [ ] Immuatable vars should declare in created construction method instead of in data declaration method
    - [ ] Logic code lines in one file should be < 150

## Practicals
* **Indention in .vue file**
  - Bad
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
  // or
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
  - No indent first line (except in html)
  - One break line after each tag

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
  - Use this is unnessarily in template
  - Bad
  ```js
    <button @click="this.next()">Click me</button>
  ```
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

## **Reference**
  - https://github.com/feross/standard/blob/master/RULES.md#javascript-standard-style 
  - https://github.com/airbnb/javascript 
  - https://vuejs.org/v2/style-guide/
  - https://gist.github.com/kashifrazzaqui