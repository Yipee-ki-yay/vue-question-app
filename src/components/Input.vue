<template>
    <div>
        <label>
            <input :type="type" 
                   :value="answer"
                   v-model="picked"
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
            picked: String,
            index: [Number, String]
        },
        data() {
            return {

            }
        },
        methods: {
            onPicked(e) {
                this.$emit('pickedradio', {
                    isPicked: e.target.value,
                    num: this.index            
                })
            }
        }
    }
</script>