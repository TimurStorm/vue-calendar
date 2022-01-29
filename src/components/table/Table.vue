<template>
    <div id="vue_calendar_table">
        <Column
            v-for="n in 7"
            :key="n"
            :workHours="workHours"
            :selected="n == 4"
        />
    </div>
</template>

<script>
import Column from './Column.vue'

export default {
    name: "Table",
    props: {
        currentDay: Number,
        currentMonth: Number,
        workHours: Array,
    },
    components:{
        Column
    }
}
</script>

<style scoped>

</style>