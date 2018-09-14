# Vuejs Coding Style Guide

[![js-standard-style](https://cdn.rawgit.com/standard/standard/master/badge.svg)](https://github.com/standard/standard)
<img src="https://vuejs.org/images/logo.png" height="60" />

This is summary of best practicals based on [standard](https://github.com/standard/standard) JavaScript
rules and [Vuejs style guide](https://vuejs.org/v2/style-guide/)

There are some adjustment for enhancing the readability of code and make us fell more comfortable when follow this styleguide.

StyleGuide is divided by 3 parts
- Strict Rules: You should strictly follow this convention because this part will improve lots of quality codes.
- EEEE: It's compulsory but this is the most common situations you may met, follow this part to improve xxx
- Practicals: Consider and apply it is suitable with project

## Rules
* **Follow standard javascript rule**
* **Follow Essential and Strongly Recommended in StyleGuide Vuejs**

## EEEE
* **Always use 2 spaces** for indentation.
  ```js
  function hello (name) {
    console.log('hi', name)
  }
  ```
  ```html
  <div class="container">
    <div class="row">
      ...
    </div>
  </div>
  ```
  ```scss
  .btn {
    &--blue {
      color: blue;
    }
    &--green {
      color: blue;
    }
  }
  ```

* **Use single quotes for strings in js and double quotes in html, css** except to avoid escaping.
  ```js
  console.log('hello there')
  $("<div class='box'>")
  ```
