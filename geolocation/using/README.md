## The geolocation object

```js
if ("geolocation" in navigator) {
  /* geolocation is available */
} else {
  /* geolocation IS NOT available */
}
```

### Getting the current position

```js
navigator.geolocation.getCurrentPosition(function(position) {
  do_something(position.coords.latitude, position.coords.longitude);
});
```

### Watching the current position

```js
var watchID = navigator.geolocation.watchPosition(function(position) {
  do_something(position.coords.latitude, position.coords.longitude);
});

navigator.geolocation.clearWatch(watchID);
```

### Fine tuning response

```js
function geo_success(position) {
  do_something(position.coords.latitude, position.coords.longitude);
}

function geo_error() {
  alert("Sorry, no position available.");
}

var geo_options = {
  enableHighAccuracy: true, 
  maximumAge        : 30000, 
  timeout           : 27000
};

var wpid = navigator.geolocation.watchPosition(geo_success, geo_error, geo_options);
```

## Describing a position

The user's location is described using a `Position` object referencing a `Coordinates` object.

## Handling errors

```js
function errorCallback(error) {
  alert('ERROR(' + error.code + '): ' + error.message);
};
```
