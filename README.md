# rolldate-full [![npm](https://img.shields.io/npm/v/rolldate-full.svg)](https://www.npmjs.com/package/rolldate-full) [![npm](https://img.shields.io/npm/dm/rolldate-full.svg)](https://www.npmjs.com/package/rolldate-full)
This plugin is a new version of rolldate (jquery-date). It is mainly used to solve the problem that the previous version of the parameter design is not reasonable, the sliding efficiency is not high, it depends on jquery, there is no optional theme style, and the callback function is added to make the plugin more flexible.

## Usage
### es6
```js
import Rolldate from 'rolldate'
new Rolldate({
  el:'#date'
})
```
### commonJS
```js
var Rolldate = require('rolldate');
new Rolldate({
  el:'#date'
})
```
### amd
```js
require(['rolldate'],function(Rolldate){
  new Rolldate({
    el:'#date'
  })
})
```
### cmd
```js
seajs.use('rolldate',function(undefined){
    //插件没有遵循cmd规范，这里的Rolldate是全局的
    new Rolldate({
      el:'#date'
    })
});
```
### Options
- el:  No | null | The plugin's dom element is bound. The plugin uses document.querySelector internally. <br> You can also pass the dom element object directly. Only a single dom element is supported.
- format: | No | 'YYYY-MM-DD' | Date format, unlimited. Rule: year-YYYY month-MM day-DD hour-hh minute-mm second-ss separated by /,-, space,:, can be combined at will
- typeMonth: | No | shows the text value of the month. Values: 'numeric','text' (default 'numeric')
- localeMonth: | No | textual names of the months to be displayed in the month column. Depends on typeMonth = 'text'. Сan be a string or an array. Example: "January_February_March_April_May_June_July_August_September_October_November_December" or ["January", "February", "March", "April", "May", "June", "July", "August", "September", "October", "November", "December"]
- beginYear: | No | 2000 | date start year
- endYear | No | 2100 | date end year
- value | No | null | The default value for date initialization, such as '2018-03-18'
- lang | No | Year, month, day ... | Configure plugin language, default: title: 'Select date', cancel: 'Cancel', confirm: 'Confirm', <br> year: 'year', month: ' Month ', day:' day ', hour:' hour ', min:' minute ', sec:' second 'minStep|否|1|分钟按指定数分隔
- init | No | null | Callback function before plugin trigger, return false can prevent plugin execution
- moveEnd | No | null | Callback function after plugin scroll, function returns a parameter (better-scroll instance)
- confirm | No | null | The callback function before the confirmation button is triggered, return false can prevent the plugin from executing, <br> return other values to modify the date, the function returns a parameter (the selected date)
- cancel | No | null | Callback function triggered when the plugin cancels
- trigger | No | 'tap' | By default, tap is used to resolve the 300ms delay of mobile click events. You can select tap to replace tap. Note that using tap will prevent other bound click events from firing
- show | No | none | active trigger plugin, when trigger is tap, active trigger plugin should use this method
- hide | No | None | Proactively hide plugins

### Example
```js
let rd = new Rolldate({
    el: '#date',
    format: 'YYYY-MM-DD',
    beginYear: 2000,
    endYear: 2100,
    minStep:1,
    lang:{title:'Select date'},
    trigger:'tap',
    init: function() {
      console.log('plugin start');
    },
    moveEnd: function(scroll) {
      console.log('End of scroll');
    },
    confirm: function(date) {
      console.log('OK button trigger');
    },
    cancel: function() {
      console.log('Plug-in canceled');
    }
});
rd.show();
rd.hide();

```
