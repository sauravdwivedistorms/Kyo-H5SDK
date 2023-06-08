# Kyō H5SDK
Kyō H5SDK is lightweight library that is supposed to seamlessly bind Kyō Web App and Android/iOS App with hosted games via postMessage protocol.

Current Static CDN https://assets.kyo.games/H5SDK.js

The recommended way to use it in your game is to simply add it as third party script.
```js
<head>
<!-- ... -->
<script type="text/javascript" src="https://assets.kyo.games/H5SDK.js"></script>
  <!-- ... -->
</head>
```
When added, it creates ```window.H5SDK``` global object that contains methods to call.

# APIs
* ```H5SDK.init()```
 
  On game start, send the message that the game has been initialized. For now, this call is optional.
  
  For example:
  
  ```js
  constructor() {
    // ...
    H5SDK.init();
    // ...
  }
  ```
* ```H5SDK.update({ SCORE: <value>})```
 
  On score update, send the message with the new score. This helps to keep a log of scores, every 5 seconds which helps the backend to detect anomalies. For now, this call is optional.
  

* ```H5SDK.submit({ SCORE: <value> , SCORE_DATA: <JSON value>})```
  
  Call this function when the game is over. It sends a message about the user's game score and score data. Where ```<value>``` - numeric integer value of the current game score. 
  If string or float numeric value is sent, there will be an attempt to convert to an integer using ```parseInt```.
  
  ```<JSON value>``` - JSON which contains score data of every 30th second. Both key and values should be a numeric integer value.
  
  
  Passing ```SCORE_DATA``` isn't required anymore.
  
  For example:
  ```js
  // random method name that calls game score sreen logic 
  showGameScore() {
    // ...
    H5SDK.submit({ 
      SCORE: 28
    });
    // ...
  }
  ```
