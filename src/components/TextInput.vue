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
                text: ''
            };
        },
        methods: {
            updateText() {
                this.update(this.text);
            }
        }
    };
</script>
