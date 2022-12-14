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