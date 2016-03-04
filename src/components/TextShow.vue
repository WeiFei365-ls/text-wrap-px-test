<template>
    <div class="text-wrap-px-show">
        <br />
        <div class="panel panel-default">
            <div class="panel-body">
                <span v-for="row in textRows" v-bind:class="updateClass" v-bind:style="updateStyle" class="text-row">{{row}}<br/></span>
            </div>
        </div>

        <span class="text-one-row" v-bind:class="updateClass" v-bind:style="updateStyle">{{showText}}</span>
    </div>
</template>

<script>
    var TextWrapPX = require('text-wrap-px');
    var _ = require('lodash');

    export default {
        name: 'TextShow',
        props: {
            text: {
                type: String,
                required: true
            },
            options: {
                type: Object
            }
        },
        data() {
            return {
                textRows: []
            };
        },
        computed: {
            showText() {
                var _opts = _.merge({}, this.options) || {};
                if (_opts.parent) {
                    _opts.parent = this.$el;
                }

                this.textRows = TextWrapPX(this.text, _opts);

                return this.text;
            },
            updateStyle() {
                return _.get(this.options, 'style') || {};
            },
            updateClass() {
                return this.options.class || '';
            }
        }
    };
</script>

<style>
.text-row,
.text-one-row {
    background-color: #f2f2f2;
}

.text-one-row {
    white-space: nowrap;
    margin-right: 50px;
}

.text-wrap-px-show {
    margin-bottom: 50px;
}
</style>
