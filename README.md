# POSTCSS CRASH ([Docs](https://postcss.org/))

## Installation Instructions
- It is included by default in most tools like NextJS, Vite etc.
- For static node projects we can install it as follows:
 ```bash
    yarn add -D postcss postcss-cli
 ```
- Make an input css file say `input.css` which will be input to `post-css` parser which will produce a output css file in the location we specify in css parse script.
- In [package.json](package.json), setup the following script:
 ```json
"scripts": {
    "build:css": "postcss src/input.css -o dist/styles.css",
    "watch:css": "postcss src/input.css -o dist/styles.css -w"
},
 ``` 
  - The `build` script will take input css and build an output css after applying all js plugins we used in postcss.(We can name script anything).
  - The `watch` script is for our dev environment, where we don't want to manually run the build script for every change o this script because of `-w` flag will watch input css for change and build output.

## Using Plugins
- First we install the npm package of required plugin as dev dependency.
- Then, we make [postcss.config.js](postcss.config.js) file, where we import and then export the plugins to be used.
   1. ### autoPrefixer
      -  plugin to parse CSS and add vendor prefixes to CSS rules. For example `::placeholder` property is not fully supported by all browsers, so we in normal css would have to manually provider vendor `webkits` like `moz`, `ms` for Firefox, Edge etc. With this plugin, we don't need to do so, postcss will automatically add these.
   2. ### postcss-preset-env
      - It allows use to use `modern css` by converting them to something most browsers can understand. Like: `custom-selector`, `custom-media` queries and `nested css`.
   3. ### precss
      - It allows to use `Sass-like` markup and staged CSS features in CSS. 
   4. ### postcss-import
      - It allows to import local css files in another css file. In our case, we have made 2 css files. One called [vars.css](src/vars.css) where we store all `sass variables` and [card.css](src/card.css) where all card styles are present. These are then imported to [input.css](src/input.css) file. 