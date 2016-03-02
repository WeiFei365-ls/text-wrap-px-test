<template>
    <div class="text-wrap-px-show">
        <input v-model="showText" class="hidden">
        <ul v-for="row in textRows" class="list-group">
            <li class="list-group-item">{{row}}</li>
        </span>
    </div>
</template>

<script>
    var textWrap = require('text-wrap-px');
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

                this.textRows = textWrap(this.text, _opts);
                return '';
            }
        }
    };
</script>
