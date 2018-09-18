<template>
    <div>
      <h2>Итого</h2>
      <hr>
      <table class="table table-bordered">
        <tr>
          <td>Вопрос</td>
          <td>Ваш ответ</td>
        </tr>
        <tr>
          <td>{{ firstTitle }}</td>
          <td>{{ radioResult }}</td>
        </tr>
        <tr>
          <td>{{ secondTitle }}</td>
          <td>
            [
            <span v-for="checkbox in checkboxArr">{{ checkbox + " " }}</span>
            ]
          </td>
        </tr>   
      </table>
    </div>
</template>

<script>
    export default {
        props: {
            firstTitle: String,
            secondTitle: String,
            radioResult: Number,
            checkboxArr: Array
        }
    }    
</script>