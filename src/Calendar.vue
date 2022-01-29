<template>
    <div id="vue_calendar">
        <div class="calendar_cont" id="hours">
            <Hours
                :workHours="workHours"
            />
        </div>
        <div class="calendar_cont">
            <Header 
                :currentDay="currentDay"
                :currentMonth="currentMonth"
                :selectDay="selectDay"
                :holidays="holidays"
            />
            <Table
                :currentDay="currentDay"
                :currentMonth="currentMonth"
                :workHours="workHours"
            />
        </div>
    </div>
</template>

<script>
import Header from './components/header/Header.vue'
import Hours from './components/hours/Hours.vue'
import Table from './components/table/Table.vue'

export default {
    name: 'Calendar',
    components:{
        Header,
        Hours,
        Table,
    },
    props: {
        workHours: Array,
        holidays: Array,
    },
    data(){
        return {
            currentDay: 1,
            currentMonth: 0,
        }
    },
    created() {
        let date = new Date()
        this.currentDay = date.getDate()
        this.currentMonth = date.getMonth()
    },
    methods: {
        selectDay(selected){
            this.currentDay = selected.day
            this.currentMonth = selected.month
        },
    },
}
</script>

<style scoped>
#vue_calendar{
    overflow-y: auto;
    height: calc(100% - 35px);
    min-width: 320px;
}
#hours{
    margin-top:calc(4vh + 15px);
}
.calendar_cont{
    float: left;
}
</style>