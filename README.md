# Slick for Vue.js

## Vue support

Supports only Vue >= 2

## Installation and usage

    $ npm install vue-date-range-calendar

***NOTE***: `vue-date-range-calendar` official package appears to use `jquery` as a dependency in package.json,
despite it would be more appropriate to use it as a peer dependency to avoid possibility of using multiple
versions of jquery. Be aware of that. When using `webpack` you can solve this problem with aliases.

```javascript
import VueDateRangeCalendar from 'vue-date-range-calendar';

new Vue({

    components: { VueDateRangeCalendar },

    data() {
        return {
            calendarOptions: {
                lang: "en",
                theme: "default-theme",
                themeContext: this,
                startDate: moment(),
                endDate: moment().add('months', 12),
                start : "+7",
                startRangeWidth : 3, 
                minRangeWidth: 1,
                maxRangeWidth: 14,
                weekends: true,
                autoHideMonths: false,
                visible: true,
                trigger: null
            }
        };
    },

    // All slick methods can be used too, example here
    methods: {
        onChange(data) {
            console.log(data);
        }
    },
});
```

```html
<vue-date-range-calendar
  :options="calendarOptions"
  @change="onChange">
</vue-date-range-calendar>
```

If you need, you can import calendar styles too:

```javascript
import `node_modules/vue-date-range-calendar/calendar.module.css`;
```
