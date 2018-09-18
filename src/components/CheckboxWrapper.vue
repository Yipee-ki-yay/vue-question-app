<template>
    <div>
      <h2>{{ title }}</h2>
      <hr>
      <div>
        <checkbox-input v-for="(answer, index) in obj.answers"
                        v-bind:key="index"
                        :answer="answer"
                        :index="index"
                        :type="obj.type"
                        @pickedbox="setCheckedRes($event, index)"
        >        
        </checkbox-input>
      </div>
      <hr>
      <button class="btn btn-primary" 
              @click="isShow"
              :disabled="!isCheckbox"
              >Next</button>
    </div>
</template>

<script>
    import CheckboxInput from './Checkbox'

    export default {
        props: {
            title: String,
            obj: Object,
            isCheckbox: Boolean
        },
        data() {
            return {
                show: true,
                // isPicked: ''
            }
        },
        methods: {
            setCheckedRes(data, index) {
                // this.isPicked = data.isCheck;

                this.$emit('pickedpickedbox', {
                    isCheck: data.isCheck,
                    index: index
                });
            },
            isShow() {
                this.$emit('showshow');
            }
        },
        // computed: {
        //     isSomeTrue() {
        //         return this.checkboxArr.some(item => item == true );
        //     }
        // },
        components: {
            CheckboxInput            
        }
    }
</script>