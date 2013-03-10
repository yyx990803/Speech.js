# Speech.js

Simple wrapper for Chrome's web speech recoginition API.

<a href="http://sketch.evanyou.me/speech/" target="_blank">Demo</a>

When trying `example.html` you need to open it via a http/https server.

### Usage

``` js

// all options default to false
var speech = new Speech({
    debugging: true, // will console.log all results
    continuous: true, // will not stop after one sentence
    interimResults: true, // trigger events on iterim results
    autoRestart: true // recommended when using continuous:true
                      // because the API sometimes stops itself
                      // possibly due to network error.
})

// simply listen to events
// chainable API
speech
    .on('start', function () {
        console.log('started')
    })
    .on('end', function () {
        console.log('ended')
    })
    .on('interimResult', function (msg) {
        document.body.innerHTML = msg
    })
    .on('finalResult', function (msg) {
        document.body.innerHTML = msg
    })
    .start()

```