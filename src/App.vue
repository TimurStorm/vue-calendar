<template>
  <div id="app">
    <div id="header">Vue Calendar</div>
    <Calendar
      :workHours="workHours"
      :holidays="holidays"
    />
  </div>
</template>

<script>
import Calendar from './Calendar.vue'

export default {
  name: 'App',
  components: {
    Calendar
  },
  data(){
    return {
      workHours: [7,8,9,10,11,12,13,14,15,16,17,18,19,20,21,22,23], // рабочие часы
      holidays: [
        [1,2,3,4,5,6,7,8,9,15,16,22,23,29,30], // выходные в январе
        [5,6,12,13,19,20,25,27] // выходные в феврале
      ]
    }
  }
  
}
</script>

<style>
#app {
    margin: 50px 10px;
    background: white;
    border-radius: 15px;
    padding: 25px 17px;
}
</style>
