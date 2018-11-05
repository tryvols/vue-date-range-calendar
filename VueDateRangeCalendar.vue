<template>
    <div></div>
</template>

<script>
const moment = require('moment');
try {
window.$ = window.jQuery = require('jquery');
require('jquery-ui-dist/jquery-ui');
require('jquery-ui-touch-punch/jquery.ui.touch-punch');
require('./calendar');
} catch(e) {}

export default {
    mounted() {
        $(this.$el).rangeCalendar(this.init());
    },
    props: {
        options: {
            type: Object,
            default () {
                return {};
            }
        }
    },
    methods: {
        init() {
            return {
                lang: this.options.lang || 'en',
                theme: this.options.theme || 'default-theme',
                themeContext: this,
                startDate: this.options.startDate || moment(),
                endDate: this.options.endDate || moment().add('months', 12),
                start: this.options.start || '+7',
                startRangeWidth: this.options.startRangeWidth || 3,
                minRangeWidth: this.options.minRangeWidth || 1,
                maxRangeWidth: this.options.maxRangeWidth || 14,
                weekends: this.options.weekends || true,
                autoHideMonths: this.options.autoHideMonths || false,
                visible: this.options.visible || true,
                trigger: this.options.trigger || null,
                changeRangeCallback: this.onChange
            }
        },
        onChange(target, range) {
            this.$emit('change', { target, range });
        }
    }
}
</script>
