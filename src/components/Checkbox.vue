<template>
    <div>
        <label>
            <input :type="type" 
                   :value="answer"
                   @input="onPicked"
                   >
            {{ answer }}
        </label>
    </div>
</template>

<script>
    export default {
        props: {
            answer: String,
            type: String,
            index: [Number, String]
        },
        methods: {
            onPicked($event) {
                this.$emit('pickedbox', {
                    isCheck: $event.target.checked
                });
            }
        }
    }
</script>