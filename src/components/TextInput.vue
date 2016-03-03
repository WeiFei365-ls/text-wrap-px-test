<template>
    <div class="text-wrap-px-input">
        <textarea v-model="text" v-on:keyup="updateText" class="text-wrap-px-input form-control" rows="5"></textarea>
    </div>
</template>

<script>

    export default {
        name: 'TextInput',
        props: {
            update: {
                type: Function,
                required: true
            }
        },
        data() {
            return {
                text: 'Deburrs string by converting latin-1 supplementary letters to basic latin letters and removing combining diacritical marks.'
            };
        },
        methods: {
            updateText() {
                this.update(this.text);
            }
        }
    };
</script>
