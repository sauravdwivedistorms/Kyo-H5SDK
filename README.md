# Kyō H5SDK
Kyō H5SDK is lightweight library that is supposed to seamlessly bind Kyō Web App and Android/iOS App with hosted games via postMessage protocol.
Current API CDN https://assets.skibbre.com/media/h5Sdk.js

The recommended way to use it in your game is to simply add it as third party script.
```
<head>
<!-- ... -->
<script type="text/javascript" src="https://assets.kyo.games/h5Sdk.js"></script>
  <!-- ... -->
</head>
```
When added, it creates ```window.H5SDK``` global object that contains methods to call.

# APIs
* ```H5SDK.init()```
 
  On game start, send the message that the game has been initialized. For now, this call is optional.
  
  For example:
  
  ```
  constructor() {
    // ...
    H5SDK.init();
    // ...
  }
  ```
* ```H5SDK.submit({ SCORE: <value> , SCORE_DATA: <JSON value>})```
  
  On every game level end or when the game is over it sends a message about the user's current game score. Where ```<value>``` - numeric integer value of the current game score. 
  If string or float numeric value is sent, there will be an attempt to convert to an integer using ```parseInt```
  
  For example:
  ```
  // random method name that calls game score sreen logic 
  showGameScore() {
    // ...
    H5SDK.submit({ SCORE: 128 });
    // ...
  }
  ```
