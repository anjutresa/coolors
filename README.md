# Colors are cool

KISS, customizable and extensible module for do colorful console.log only for NodeJS. Simple, easy.

- Auto-detects color support
- Clean and focused
- Extensible and configurable

![screenshot](https://github.com/codersbrothers/coolors/raw/master/screenshot.png)

## Install

```sh
$ npm i --save coolors
```

## Usage

```js
var coolors = require('coolors');
console.log(coolors('My cool console log', 'red'));
```

#### Configurable

```js
var coolors = require('coolors');
console.log(coolors('My cool console log', {
    text: 'yellow',
    background: 'red',
    bold: true,
    underline: true,
    inverse: true,
    strikethrough: true
}));
```
Check example.js for view more examples

## Options

#### Decorators
Styles will display correctly if font used in your console supports them.

* bold
* dim
* italic *(not widely supported)*
* underline
* inverse
* hidden
* strikethrough *(not widely supported)*

We can use like:

```js
var coolors = require('coolors');
console.log(coolors('My cool console log', 'bold'));
```

#### Colors

<table>
  <thead><th>Foreground</th><th>Background</th><th></th></thead>
  <tbody>
    <tr><td>black</td><td>bgBlack</td><td><img src="http://medyk.org/colors/000000.png" width="30" height="30" /></td></tr>
    <tr><td>red</td><td>bgRed</td><td><img src="http://medyk.org/colors/800000.png" width="30" height="30" /></td></tr>
    <tr><td>green</td><td>bgGreen</td><td><img src="http://medyk.org/colors/008000.png" width="30" height="30" /></td></tr>
    <tr><td>yellow</td><td>bgYellow</td><td><img src="http://medyk.org/colors/808000.png" width="30" height="30" /></td></tr>
    <tr><td>blue</td><td>bgBlue</td><td><img src="http://medyk.org/colors/000080.png" width="30" height="30" /></td></tr>
    <tr><td>magenta</td><td>bgMagenta</td><td><img src="http://medyk.org/colors/800080.png" width="30" height="30" /></td></tr>
    <tr><td>cyan</td><td>bgCyan</td><td><img src="http://medyk.org/colors/008080.png" width="30" height="30" /></td></tr>
    <tr><td>white</td><td>bgWhite</td><td><img src="http://medyk.org/colors/c0c0c0.png" width="30" height="30" /></td></tr>
  </tbody>
</table>

We can use like:

```js
var coolors = require('coolors');
console.log(coolors('My cool console log', 'red'));
console.log(coolors('My cool console log 2', 'bgRed'));
```

### Extend
You can extend and create your own custom logs creating something like this

```js
// coolorsExtended.js
var coolors = require('coolors');
function rainbowLog(msg){
    var colorsText = coolors.availableStyles().text;
    var rainbowColors = colorsText.splice(3);
    var lengthRainbowColors = rainbowColors.length;
    var msgInLetters = msg.split('');
    var rainbowEndText = '';
    var i = 0;
    msgInLetters.forEach(function(letter){
        if(letter != ' '){
            if(i === lengthRainbowColors) i = 0;
            rainbowEndText += coolors(letter, rainbowColors[i]);
            i++;
        }else{
            rainbowEndText += ' ';
        }
    });
    return rainbowEndText;
}
coolors.addPlugin('rainbow', rainbowLog);
module.exports = coolors;
```

```js
// app.js
var coolorsExtended = require('./coolorsExtended');
console.log(coolorsExtended('This its a creative example extending core with a cool rainbow style', 'rainbow'));
console.log(coolorsExtended('My cool console log', 'red'));
```

If you want extend more you can check [this](http://misc.flogisoft.com/bash/tip_colors_and_formatting)

#### TODO
* Add example of extend to do a console log with differents colors for type words. Something like:
     
        { 
             special: 'cyan',
             number: 'yellow',
             boolean: 'yellow',
             undefined: 'grey',
             null: 'bold',
             string: 'green',
             date: 'magenta',
             regexp: 'red' 
        }   

#### License

The MIT License (MIT)

Copyright (c) 2014 Coders Brothers

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
