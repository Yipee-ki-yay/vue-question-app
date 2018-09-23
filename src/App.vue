<template>
  <div class="wrapper">
    <transition name="fade" mode="out-in" appear>  
      <radio-wrapper v-if="!firstShow"
                    :title="info[0].title"
                    :obj="info[0]"
                    :picked="picked"
                    @pickedpickedradio="changePicked(index, $event)"
                    @showshow="isFirstShow()"
      ></radio-wrapper>
    
      <checkbox-wrapper v-if="firstShow && !secondShow"
                        :title="info[1].title"
                        :obj="info[1]"
                        :isCheckbox="isCheckboxed"
                        @pickedpickedbox="setCheckedRes($event)"
                        @showshow="isSecondShow()"
      ></checkbox-wrapper> 

      <app-final v-if="firstShow && secondShow"
                :firstTitle="info[0].title"
                :secondTitle="info[1].title"
                :radioResult="results[0].radioNum"
                :checkboxArr="checkboxNum"
      ></app-final>
    </transition>
  </div>
</template>

<script>
  import RadioWrapper from './components/RadioWrapper';
  import CheckboxWrapper from './components/CheckboxWrapper.vue';
  import AppFinal from './components/Final.vue';

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
          }
        ],
        picked: '',
        checkboxNum: [],
        firstShow: false,
        secondShow: false,
        isCheckboxed: false        
      }
    },
    methods: {
      changePicked(index, data) {
        this.picked = data.isPicked;
        this.results[0].radioNum = data.num;
      },
      setCheckedRes(data) {
        // this.checkboxNum[data.index] = data.isCheck;
        this.$set(this.checkboxNum, data.index, data.isCheck);
        this.isSomeTrue();
        // console.log(this.checkboxNum);
      }
    },
    beforeMount() {
      for(let i = 0; i < this.info[1].answers.length; i++) {
        this.checkboxNum[i] = false;
        console.log('bm');
      }
    },
    computed: {
      isFirstShow() {
        return this.firstShow = true;
        // console.log(this.firstShow);
      },
      isSecondShow() {
        return this.secondShow = true;
        // console.log(this.secondShow);
      },
      isSomeTrue() {
        console.log('bam!');
        if (this.checkboxNum.some(item => item == true )) {
          return this.isCheckboxed = true;
          console.log(this.isCheckboxed);
        } else {
          return this.isCheckboxed = false;
          console.log(this.isCheckboxed);
        }
      }
    },
    components: {
      RadioWrapper,
      CheckboxWrapper,
      AppFinal
    }
  }
</script>

<style scoped>
  .wrapper {
    max-width: 1200px;
    margin-left: auto;
    margin-right: auto;  
  }

  .fade-enter {
    opacity: 0;
  }
  .fade-enter-active {
    transition: opacity .5s;
  }
  .fade-enter-to {

  }
  .fade-leave {

  }
  .fade-leave-active {
    transition: opacity .5s;
  }
  .fade-leave-to {
    opacity: 0;
  }

</style>