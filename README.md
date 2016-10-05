## browserify(パッケージ依存解決ツール)

```
npm init
npm install --save-dev browserify
```

依存関係解決ができるか確認

first.js、second.jsを作成する

first.js

```
var second = require('./second.js');
second.hello();
```

second.js

```
module.exports.hello = function() {
    console.log('Hello from second.js!');
}
```

実行

```
node_modules/.bin/browserify first.js -o bundle.js
```

bundle.js

```
(function e(t,n,r){function s(o,u){if(!n[o]){if(!t[o]){var a=typeof require=="function"&&require;if(!u&&a)return a(o,!0);if(i)return i(o,!0);var f=new Error("Cannot find module '"+o+"'");throw f.code="MODULE_NOT_FOUND",f}var l=n[o]={exports:{}};t[o][0].call(l.exports,function(e){var n=t[o][1][e];return s(n?n:e)},l,l.exports,e,t,n,r)}return n[o].exports}var i=typeof require=="function"&&require;for(var o=0;o<r.length;o++)s(r[o]);return s})({1:[function(require,module,exports){
var second = require('./second.js');
second.hello();


},{"./second.js":2}],2:[function(require,module,exports){
module.exports.hello = function() {
    console.log('Hello from second.js!');
}

},{}]},{},[1]);

```



test.htmlを作成し、budle.jsを読み込む  

```
<html>
<body>
    <script src="bundle.js"></script>
</body>
</html>
```


ブラウザでアクセスしコンソールを確認。正しく表示されたか確認
