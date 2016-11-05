# Material Datetime Picker 

[https://ripjar.github.io/material-datetime-picker/](https://ripjar.github.io/material-datetime-picker/)


[![Status][status]](https://travis-ci.org/ripjar/material-datetime-picker) 
[![Package][npm]](https://www.npmjs.com/package/material-datetime-picker)

A take on the material design date picker modal, built for the web.

Works well with Materialize, or standalone.

![Time][date] ![Time][time]

## Installation

```
npm install material-datetime-picker
```

#### Dependencies

The picker depends on Google's Material Design icons (packaged with Materialize), or included in the `head` of the document;

```html
<link href="https://fonts.googleapis.com/icon?family=Material+Icons" rel="stylesheet">
```

--- 

For best results also include Google's Material Font `Roboto`;

```html
<link href='https://fonts.googleapis.com/css?family=Roboto' rel='stylesheet' type='text/css'>
```

---

`Rome.js` and `moment` are required by the picker to handle date and time. 

It is recommended to use the picker as an ES6 module using `import` or `require` (documented below). With this method the script will import it's own dependencies as required. 

Alternatively, there is a packaged script `/dist/js/datepicker.standalone.min.js`, which will include dependencies alongside the library code.

To include them yourself you can also use the dependency free version `/dist/js/datepicker.min.js`.

## Usage

### Manual (recommended)

The picker can be instantiated and interacted with manally;
    
```javascript
import MaterialDateTimePicker from 'material-datetime-picker';

const picker = new MaterialDateTimePicker()
    .on('submit', (val) => console.log(`data: ${val}`))
    .on('open', () => console.log('opened'))
    .on('close', () => console.log('closed'));

document.querySelector('.c-datepicker-btn')
    .on('click', () => picker.open());        
```

---

### As form input

The picker is decoupled from any single form element for simplicity. However, it should be simple to link the picker to a form input or button. For instance, given the input element `<input class="c-datepicker-input" />`, the following could be written;
    
```javascript
import MaterialDateTimePicker from 'material-datetime-picker';

const input = document.querySelector('.c-datepicker-input');
const picker = new MaterialDatePicker()
    .on('submit', (val) => {
      input.value = val.format("DD/MM/YYYY");
    });

input.addEventListener('focus', () => picker.open());      
```

## Options
    
All options are optional, including the `el`.

```javascript
{
    // element to attach the datepicker. this element will receive 
    // events when the data changes. If an input element, will be 
    // populated with formatted date and time chosen
    el: document.querySelector('.c-datepicker-btn'),
    // if `el` is set, `openedBy` is the event on `el` that will
    // open the picker, eg. `click` or `focus`
    openedBy: 'focus',
    // if `el` is set, the format used to display the datetime in the input, // or set as a data attribute
    format: 'dd/MM/YY', 
    //  the default value of the picker
    default: moment(),
    // the container to append the picker
    container: document.body,    
    // cosmetic classes that can be overriden
    // mostly used for styling the calendar
    styles: {
        scrim: 'c-scrim',
        back: 'c-datepicker__back',
        container: 'c-datepicker__calendar',
        date: 'c-datepicker__date',
        dayBody: 'c-datepicker__days-body',
        dayBodyElem: 'c-datepicker__day-body',
        dayConcealed: 'c-datepicker__day--concealed',
        dayDisabled: 'c-datepicker__day--disabled',
        dayHead: 'c-datepicker__days-head',
        dayHeadElem: 'c-datepicker__day-head',
        dayRow: 'c-datepicker__days-row',
        dayTable: 'c-datepicker__days',
        month: 'c-datepicker__month',
        next: 'c-datepicker__next',
        positioned: 'c-datepicker--fixed',
        selectedDay: 'c-datepicker__day--selected',
        selectedTime: 'c-datepicker__time--selected',
        time: 'c-datepicker__time',
        timeList: 'c-datepicker__time-list',
        timeOption: 'c-datepicker__time-option',
        clockNum: 'c-datepicker__clock__num'
    },
    // date range to allow (see rome validator factories)
    dateValidator: null       
}
```

## License

MIT


[date]: https://github.com/ripjar/material-datepicker/raw/master/demo/date.png "Date select image"
[time]: https://github.com/ripjar/material-datepicker/raw/master/demo/time.png "Time select image"
[status]: https://api.travis-ci.org/ripjar/material-datetime-picker.svg "Build Status"
[npm]: https://img.shields.io/npm/v/material-datetime-picker.svg "Package"
