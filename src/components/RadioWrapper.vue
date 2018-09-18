<template>
    <div>
      <h2>{{ title }}</h2>
      <hr>
      <div>
      <app-input v-for="(answer, index) in obj.answers"
                 v-bind:key="index"
                 :answer="answer"
                 :index="index"
                 :type="obj.type"
                 :picked="picked"
                 @pickedradio="changePicked(index, $event)"
      ></app-input>
      </div>
      <hr>    
      <button class="btn btn-primary" 
              @click="isShow"
              :disabled="!picked"
              >Next</button>
    </div>
</template>

<script>
    import AppInput from './Input';

    export default {
        props: {
            title: String,
            obj: Object,
            picked: String
        },
        data() {
            return {
                show: true
            }
        },
        methods: {
            changePicked(index, data) {
                this.$emit('pickedpickedradio', {
                    isPicked: data.isPicked,
                    num: data.num     
                });
            },
            isShow() {
                this.$emit('showshow');
            }
        },
        components: {
            AppInput,
        }
    }
</script>