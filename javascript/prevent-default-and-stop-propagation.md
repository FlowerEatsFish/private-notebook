# Prevent Default and Stop Propagation

- [Prevent Default and Stop Propagation](#prevent-default-and-stop-propagation)
  - [References](#references)
  - [Source code](#source-code)

## References

- [Explore DOM Events](https://domevents.dev/)

## Source code

```html
<!DOCTYPE html>

<html lang="en">

<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <meta http-equiv="X-UA-Compatible" content="ie=edge">
  <style>
    #div1, #a1, #a2 { margin: 8px; padding: 8px; display: block; line-height: 2rem; cursor: pointer; }
    #div1 { border: 2px blue solid; }
    #a1 { border: 2px red solid; }
    #a2 { border: 2px green solid; }
  </style>
  <title>EVENT TEST</title>
</head>

<body>
  <div id="div1">
    #div1
    <a id="a1" href="https://github.com/flowereatfish">#a1 Test event.preventDefault()</a>
    <a id="a2" href="https://github.com/flowereatfish">#a2 Test event.preventDefault() and event.stopPropagation()</a>
  </div>

  <script type="text/javascript">
    document.getElementById("a1").addEventListener("click", function (event) {
      event.preventDefault();
      console.log("a1 click with event.preventDefault");
    });

    document.getElementById("a2").addEventListener("click", function(event) {
      event.preventDefault();
      event.stopPropagation();
      console.log("a2 click with event.preventDefault and event.stopPropagation");
    });

    document.getElementById("div1").addEventListener("click", function(event) {
      console.log("div1 click");
    });
  </script>
</body>

</html>
```
