gulp-prefix
=========

A gulp plugin inspired by [html-prefixer](https://github.com/tivac/node-html-prefixer).

Will prefix relative urls in &lt;link&gt;, &lt;script&gt; and &lt;img&gt; tags

You can optionally pass a second argument along with the prefix string to override the default selection statements.
The default config looks like this:

```
[
  { match: "script[src]", attr: "src" },
  { match: "link[href]", attr: "href"},
  { match: "img[src]", attr: "src"},
  { match: "input[src]", attr: "src"}
]
```


###HTML
```html
<html>
  <head>
    <link href="http://cdnjs.com/some-library.css">
    <link href="css/stylesheets.css">
  </head>
  <body>
    <img src="/images/myImage.jpg"/>
    <script src="//cdnjs.com/some-library.js"></script>
    <script src="js/scripts.js"></script>
  </body>
</html>
```



###Usage
```javascript
var gulp = require('gulp'),
    prefix = require('gulp-prefix');

gulp.task('prefix', function(){
  var prefixUrl = "http://mydomain.com/assets";

  gulp.src('index.html')
    .pipe(prefix(prefixUrl, null, true))
    .pipe(gulp.dest('build'));
});
```

###Output
```html
<html>
  <head>
    <link href="http://cdnjs.com/some-library.css">
    <link href="http://mydomain.com/assets/css/stylesheets.css">
  </head>
  <body>
    <img src="http://mydomain.com/assets/images/myImage.jpg"/>
    <script src="//cdnjs.com/some-library.js"></script>
    <script src="http://mydomain.com/assets/js/scripts.js"></script>
  </body>
</html>
```

To run tests install jasmine-node globally `npm install jasmine-node -g` and run `jasmine-node spec`


License
----

MIT
    
