<template>
    <div id="app" class="container">
        <h2>Text Wrap Pixels</h2>
        <div class="row">
            <div class="text-wrap-px-options col-md-5">
                <div class="panel panel-default">
                    <div class="panel-heading">Options:</div>
                    <json-editor :anything="options" :update="updateOptions" class="panel-body"></json-editor>
                </div>
            </div>
            <div class="col-md-7">
                <div class="row">
                    <text-input :update="updateText" class="col-md-12"></text-input>
                </div>
                <div class="row">
                    <text-show :text="text" :options="options" class="col-md-12"></text-show>
                </div>
            </div>
        </div>
    </div>
</template>

<script>

import JsonEditor from './components/JsonEditor.vue';
import TextInput from './components/TextInput.vue';
import TextShow from './components/TextShow.vue';

export default {
    data() {
        return {
            options: {
                maxWidth: 100,
                splitSymbol: ' ',
                suffix: '...',
                class: 'test1 test2',
                style: {
                    fontSize: '20px'
                },
                parent: true
            },
            text: ''
        };
    },
    methods: {
        updateOptions(options) {
            this.options = options;
        },
        updateText(text) {
            this.text = text;
        }
    },
    components: {
        JsonEditor,
        TextInput,
        TextShow
    }
}

</script>

<style src="./style/bootstrap.min.css"></style>
