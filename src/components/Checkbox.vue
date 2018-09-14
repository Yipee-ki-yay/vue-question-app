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
        props: ['answer', 'index', 'type'],
        methods: {
            onPicked(e) {
                this.$emit('pickedbox');
            }
        }
    }
</script>