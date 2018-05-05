# Web chart card

- [IE-related issues](#ie-related-issues)

- [Snippets](#snippets)

---

## IE-related issues

### ECMAScript 6 (or newest) support on Internet Explorer 9~11

- HTML:

  ```html
  <script src="https://cdn.polyfill.io/v2/polyfill.min.js"></script>
  ```

[Top](#web-chart-card)

### The "oninput" event of HTML elements

This event occurs when the value of an \<input> or \<textarea> element is changed.

- Troubleshooting

  Give same function to both "onchange" and "oninput" events.

  The "oninput" event in Chrome work in real-time event, but the "onchange" event work after end an action. However, the "onchange" event in IE work in real-time event, but the "oninput" event doesn't work.

- HTML:

  ```html
  <input onchage="myFunction()" oninput="myFunction()">
  ```

- JavaScript:

  ```javascript
  function myFunction() {
      // do something...
  }
  ```

[Top](#web-chart-card)

### CSS grid layout

IE use old CSS grid layout, so the codes as follows are necessary:

- Reference: [Instantly share code, notes, and snippets](https://gist.github.com/rbnlffl)

- SCSS:

  ```scss
  $const-grid-gap: 4;

  @mixin grid-ie-calc($items, $grid-gap, $max-column) {
    $column: 1;
    $row: 1;

    @if $grid-gap > 0 {
      margin: $grid-gap / 2;

      @supports (grid-gap: $grid-gap) {
        margin: 0;
      }
    }

    @for $i from 1 through $items {
      @if $column > $max-column {
        $column: 1;
        $row: $row + 1;
      }

      :nth-child(#{$i}) {
        -ms-grid-row: $row; /* support on IE */
        -ms-grid-column: $column; /* support on IE */
      }

      $column: $column + 1;
    }
  }

  .foo {
    display: grid;
    display: -ms-grid; /* support on IE */
    grid-gap: $const-grid-gap;
    grid-template-columns: 1fr 1fr 1fr;
    -ms-grid-columns: 1fr 1fr 1fr; /* support on IE */
    grid-template-rows: 1fr 1fr;
    -ms-grid-rows: 1fr 1fr; /* support on IE */
    @include grid-ie-calc(6, $const-grid-gap ,3);
  }
  ```

[Top](#web-chart-card)

---

## Snippets

### Bouncing loader

- Reference: [30 Seconds of CSS](https://atomiks.github.io/30-seconds-of-css/#bouncing-loader)

- HTML:

  ```html
  <div class="bouncing-loader">
    <div></div>
    <div></div>
    <div></div>
  </div>
  ```

- CSS:

  ```css
  @keyframes bouncing-loader {
    from {
      opacity: 1;
      transform: translateY(0);
    }
    to {
      opacity: 0.1;
      transform: translateY(-1rem);
    }
  }
  .bouncing-loader {
    display: flex;
    justify-content: center;
  }
  .bouncing-loader > div {
    width: 1rem;
    height: 1rem;
    margin: 3rem 0.2rem;
    background: #8385aa;
    border-radius: 50%;
    animation: bouncing-loader 0.6s infinite alternate;
  }
  .bouncing-loader > div:nth-child(2) {
    animation-delay: 0.2s;
  }
  .bouncing-loader > div:nth-child(3) {
    animation-delay: 0.4s;
  }
  ```

[Top](#web-chart-card)

### Vertically and horizontally center text with CSS

- Reference: [Stack Overflow](https://stackoverflow.com/questions/8865458/how-do-i-vertically-center-text-with-css)

- CSS:

  ```css
  .foo {
    align-items: center; /* align vertical */
    display: flex;
    justify-content: center; /* align horizontal */
    text-align: center;
  }
  ```

[Top](#web-chart-card)
