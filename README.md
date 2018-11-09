# overlay.js
Quick and easy javascript loading overlay.

Ever need a quick solution to show a loading screen while you add the page? Don't want the hassle of writing your own system to keep track of the asynchronous ajax calls and page loading? Can't find a quick and easy loading GIF?

Overlay.js is for you!

## Dependancies
None

## Try it now!
https://jsfiddle.net/souramoo/3tk5vyw9/

## Usage

```
<html>
<body>
Hello
<script src="overlay.js"></script>
<script>
// do stuff
setTimeout(function(){
  overlayHide() // on load, the overlay will show. so hide it after five seconds.
}, 5000)
</script>
</body>
</html>
```

And your page will be loading!


## Functions

`overlayShow()` show the overlay. Optionally, set a tag to be able to pop it off later (for readability and to debug which callbacks never return if you get stuck on the overlay).

`overlayHide()` hide the overlay. Optionally, pop a tag from the stack.

The overlay will hide once ALL the tags in the stack have been popped. So you can fire off overlayShow for each asynchronous data load and overlayHide for each callback and the overlay will only go away once all the data calls have finished!

## Examples
```
<html>
<body>
Hello
<script src="overlay.js"></script>
<script src="jquery.js"></script>
<script>
// get some data
overlayShow()
$.getJSON( "/api/function", function( data ) {
        // do stuff with data
        console.log(data)
        overlayHide()
})

overlayShow()
$.getJSON( "/api/function2", function( data ) {
        // do stuff with data
        console.log(data)
        overlayHide()
})

// overlay will only go when both have returned, simplifying your code!

setTimeout(function(){
  overlayHide()
}, 5000)
</script>
</body>
</html>
```

