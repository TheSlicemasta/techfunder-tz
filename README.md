# techfunder-tz (VUE 2, Webpack CLI 3, SASS, BEM, Highcharts)

## Task #201608-2: 

### 1. General description

Test task consists of 2 parts:
Build HTML + styles
Create JS-component

On the first part - you need to prepare frontend interface template on basis of provided mockup, as shown on fig. 1.1. 

Fig. 1.1 - Layout overview

You can download mockup here.

On the second part - you need to build JS component which allows to build 3 kinds of charts (pie, bar, line) on basis of demo datasets and insert it into page like new blocks at the bottom side. Blocks must be similar to existing 2 blocks at the layout bottom side. Result must look like on fig. 1.2.


Fig. 1.2 - Layout with components

For charts insertion - we need to replace 2 buttons in the second block by 2 elements:
Dropdown “Chart type” : pie, bar, line
Button “Insert”


Charts must be build on basis of adding code like: 
##### <chart type=”line” data-set=””></chart>


### 2. Technologies which must be used
For assets bundling you can use any bundler that available today (gulp, webpack, browserify, npm scripts, rollup, etc.)

For styles - SCSS

Use es6(or later) version of JS

JS code must have modular structure and be based on vue.js (v2) framework and highcharts.js.


### 3. Quality Requirements
Template must look by the same way as on mockup, have the same colors, etc.
Don’t use the font from mockups, try to find the most similar free for use font

Don’t use bootstrap. Please create layout by your own.
Try to write reusable, non conflicting CSS
Layout must be cross-browser and fill the whole width of the screen for all resolutions. On large screens it must look like on mockup. On medium screens - all blocks must have the same width (2 columns). On small screens we must use just 1 column layout.



## Project setup
```
npm install
```

### Compiles and hot-reloads for development
```
npm run serve
```

### Compiles and minifies for production
```
npm run build
```

### Run your tests
```
npm run test
```

### Lints and fixes files
```
npm run lint
```
