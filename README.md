# Scss setup 
This guide demonstrates to setup SCSS using node js.

## What is Scss?
Scss is a one of the syntaxes of Sass.

## What is Sass?
__Simple:__ Sass is a css preprocessor.

__Detailed:__
Sass is an extension of CSS that adds power and elegance to the basic language. It allows you to use variables, nested rules, mixins, inline imports, and more, all with a fully CSS-compatible syntax. Sass helps keep large stylesheets well-organized, and get small stylesheets up and running quickly, particularly with the help of the Compass style library.

__URL:__
http://sass-lang.com/

##Tools Required
1. NodeJs
2. Visual Studio Code

## Installing Packages
### Step 1: Install node-sass
```
npm install -g node-sass 
```
This node module will transpile scss/sass to css.
### Step 2: Install gulp & gulp-sass
Be sure you are in the working directory before run this command, which is goin to install node_modules in the working directory.
```
npm install gulp gulp-sass 
```
Gulp is a task runner which here going to be used to watch ```scss``` files changes and transpile them to ```css``` on the fly.
## Working with Visual Studio Code
Open VS Code and then open your workspace folder and create the following directories.

1. css
2. scss

**scss** will contain scss source files **css** will contain the transpiled output.
### Setup gulp task
Now we are going to setup a gulp task which will watch **scss** folder and transpiles to ```.css``` and output the file to **css** folder whenever ```.scss``` files got new changes.

_Step 1:_ create a gulpfile.js file in the root of the workspace.

_Step 2:_ configure task

```javascript
// Sass configuration
var gulp = require('gulp');
var sass = require('gulp-sass');

gulp.task('sass', function() {
    gulp.src('scss/*.scss')
        .pipe(sass())
        .pipe(gulp.dest('css'))
});

// default task
gulp.task('default', ['sass'], function() {
   gulp.watch('scss/*.scss', ['sass']);
})
```
Now changes to the ```.scss``` files will be transpiled as ```.css``` to the **css** directive.

_Step 3:_ Visual Studio Code tasks.json

To do this open the Command Palette with ```F1``` and type in Configure Task Runner, press Enter to select it. In the selection dialog that shows up, select **Others**.

This action will create _tasks.json_ file to the **.vscode** directive.

Add/change the code as follows

```javascript
{
 "version": "0.1.0",
    "command": "gulp",
    "isShellCommand": true,
    "tasks": [
        {
            "taskName": "default",
            "isBuildCommand": true,
            "showOutput": "always",
            "isWatching": true
        }
    ]
}
```
That's it! :boom: Now you can work on your **scss** and it will automatically transpiled to **css**.

## Resources
To learn abour Sass/Scss checkout here http://sass-lang.com/guide.  
