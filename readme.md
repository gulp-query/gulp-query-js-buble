## gulp-query-js-buble
JS plugin for [gulp-query](https://github.com/gulp-query/gulp-query)

Uses [buble](https://buble.surge.sh/guide/) and [uglify](https://www.npmjs.com/package/gulp-uglify)

This plugin provides automatic source maps, concatenation, minification and compiling ECMAScript 2015 using Bublé.

P.S. Bublé is the blazing fast, batteries-included ES2015 compiler
```
npm install gulp-query gulp-query-js-buble
```

### Example
Paste the code into your `gulpfile.js` and configure it
```javascript
let build = require('gulp-query')
  , js = require('gulp-query-js-buble')
;
build((query) => {
    query.plugins([js])
      // creates js/app.js
      .js('src/js/app.js','js/','app')
    
      // creates with new name 
      .js('src/js/admin.js','js/undercover.js')
    
      // Config as object
      .js({
        from: 'src/js/main.js',
        to: 'js/',
        name: 'main'
      })
      
      // Multiple files
      .js(['src/js/app.js','src/js/main.js'],'js/')
      
      // Multiple files and concat
      .js(['src/js/app.js','src/js/main.js'],'js/concat.js')
    ;
});
```
And feel the freedom
```
gulp
gulp --production // For production
gulp watch // Watching change
gulp js // Only for js
gulp js:app // Only for app.js
gulp js:admin js:main watch // Watching change only for admin.js and main.js
...
```

### Options
```javascript
.js({
    name: "task_name", // For gulp js:task_name 
    from: "src/js/app.js", // ["src/js/f1.js", "src/js/f2.js"]
    to: "js/", // set filename "js/concat.js" -- for concat or rename
    source_map: true,
    source_map_type: 'inline',
    full: false // if set true is without compress in prod
})
```