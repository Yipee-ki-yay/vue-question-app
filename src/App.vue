<template>
  <div class="wrapper">

    <div>
      <h2>{{ this.info[0].title }}</h2>
      <hr>
      <div>
      <app-input v-for="(answer, index) in info[0].answers"
                 v-bind:key="index"
                 :answer="answer"
                 :index="index"
                 :type="info[0].type"
                 :picked="picked"
                 @pickedradio="changePicked(index, $event)"
      ></app-input>
      </div>
      <hr>    
      <button class="btn btn-primary" @click="show = !show">Next</button>
    </div>

    <div>
      <h2>{{ this.info[1].title }}</h2>
      <hr>
      <div>
        <checkbox-input v-for="(answer, index) in info[1].answers"
                        v-bind:key="index"
                        :answer="answer"
                        :index="index"
                        :type="info[1].type"
                        @pickedbox="setCheckedRes($event, index)"
        >        
        </checkbox-input>
      </div>
      <hr>
      <button class="btn btn-primary" @click="show = !show">Next</button>
    </div>

    <h2>Итого</h2>
    <hr>
    <table class="table table-bordered">
      <tr>
        <td>Вопрос</td>
        <td>Ваш ответ</td>
      </tr>
      <tr>
        <td>{{ this.info[0].title }}</td>
        <td>{{ this.results[0].radioNum }}</td>
      </tr>
      <tr>
        <td>{{ this.info[1].title }}</td>
        <td>{{ this.results[0].checkboxNum }}</td>
      </tr>   
    </table>

  </div>
</template>

<script>
  import AppInput from './components/Input';
  import CheckboxInput from './components/Checkbox';

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
        results: [
          {
            radioNum: '',
            checkboxNum: []
          }
        ],
        picked: '',
        show: true        
      }
    },
    methods: {
      changePicked(index, data) {
        this.picked = data.isPicked;
        this.results[0].radioNum = data.num;
      },
      setCheckedRes($event, index) {
        this.results[0].checkboxNum[index] = $event.target.checked;
        console.log($event.target.checked);
        console.log(this.results[0].checkboxNum);
      }
    },
    beforeMount() {
      for(let i = 0; i < this.info[1].answers.length; i++) {
        // this.results[0].checkboxNum.push(false);
        this.results[0].checkboxNum[i] = false;
        console.log('bm');
      }
    },
    components: {
      AppInput,
      CheckboxInput
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