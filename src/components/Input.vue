<template>
    <label>
        <input :type="type" 
               :value="answer"
               v-model="picked"
               @input="onPicked"
               >
        {{ answer }}
    </label>
</template>

<script>
    export default {
        props: ['answer', 'type', 'picked'],
        data() {
            return {

            }
        },
        methods: {
            onPicked(e) {
                this.$emit('pickedradio', {
                    isPicked: e.target.value 
                })
            }
        }
    }
</script>