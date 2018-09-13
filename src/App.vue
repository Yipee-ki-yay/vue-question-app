<template>
  <div class="wrapper">

    <h2>{{ this.info[0].title }}</h2>
    <hr>
    <div>
      <!-- <label>
        <input :type="info[0].type" name="" >
        {{ answer }}
      </label> -->
      <app-input v-for="(answer, index) in info[0].answers"
                 :answer="answer"
                 :type="info[0].type"    
                 :picked="picked"    
                 @pickedradio="changePicked(index, $event)"
      ></app-input>
    </div>
    <hr>
    
    <button class="btn btn-primary">Next</button>

  </div>
</template>

<script>
  import AppInput from './components/Input';

  export default {
    data() {
      return {
        info: [
          {
            type: 'radio',
            title: 'Какой тег задаёт ссылку?',
            answers: [
              'a',
              'div',
              'span',
              'img'
            ]
          },
          {
            type: 'checkbox',
            title: 'Какие из  этих тегов строчные?',
            answers: [
              'a',
              'div',
              'span',
              'img'
            ]
          }
        ],
        picked: ''        
      }
    },
    methods: {
      changePicked(index, data) {
        this.picked = data.isPicked;
      }
    },
    components: {
      AppInput
    }
  }
</script>

<style scoped>
  .wrapper {
    max-width: 1200px;
    margin-left: auto;
    margin-right: auto;  
  }
</style>