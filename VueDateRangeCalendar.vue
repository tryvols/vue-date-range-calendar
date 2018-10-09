<template>
    <div></div>
</template>

<script>
const moment = require('moment');
window.$ = window.jQuery = require('jquery');
require('jquery-ui-dist/jquery-ui');
require('jquery-ui-touch-punch/jquery.ui.touch-punch');
require('./calendar');

export default {
    mounted() {
        this.init();
        $(this.$el).rangeCalendar(this.options);
    },
    props: {
        options: {
            type: Object,
            default: {}
        }
    },
    methods: {
        init() {
            this.options.lang = 'en' || this.options.lang;
            this.options.theme = 'default-theme' || this.options.theme;
            this.options.themeContext = this;
            this.options.startDate = moment() || this.options.startDate;
            this.options.endDate = moment().add('months', 12) || this.options.endDate;
            this.options.start = '+7' || this.options.start;
            this.options.startRangeWidth = 3 || this.options.startRangeWidth;
            this.options.minRangeWidth = 1 || this.options.minRangeWidth;
            this.options.maxRangeWidth = 14 || this.options.maxRangeWidth;
            this.options.weekends = true || this.options.weekends;
            this.options.autoHideMonths = false || this.options.autoHideMonths;
            this.options.visible = true || this.options.visible;
            this.options.trigger = null || this.options.trigger;
            this.options.changeRangeCallback = this.onChange;
        },
        onChange(data) {
            this.$emit('change', data);
        }
    }
}
</script>

<style scoped lang="scss">
    @import "./style.css";
</style>