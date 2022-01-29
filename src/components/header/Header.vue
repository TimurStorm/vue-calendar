<template>
    <div id="vue_calendar_header" :key="currentDay">
        <Item
        v-for="btn in visibleBtn"
        :key="btn.day"
    
        :day="{
            'day':btn.day,
            'month': btn.month,
            }"
        :selectDay="selectDay"
        :isSelected="btn.day == currentDay"
        :isHoliday="holidays[btn.month].includes(btn.day)"
        />
    </div>
</template>

<script>
import Item from './Item.vue'

var months31 = [0,2,4,6,7,9,11]
var months30 = [3,5,8,10]

export default {
    name: "Header",
    components:{
        Item,
    },
    props:{
        currentDay: Number,
        currentMonth: Number,
        selectDay: Function,
        holidays: Array,
    },
    beforeMount(){
        this.setVisibleBtn()
    },
    watch: {
        currentDay: function(){
            this.setVisibleBtn()
        },
    },
    data(){
        return {
            visibleBtn: []
        }
    },
    methods:{
        getLastMonth(currentMonth){
            if (currentMonth == 0){
                return 11
            } else {
                return currentMonth - 1
            }
        },
        getNextMonth(currentMonth){
            if (currentMonth == 11){
                return 0
            } else {
                return currentMonth + 1
            }
        },
        setVisibleBtn(){
            this.visibleBtn = []

            for ( let count = 0; count < 7 ; count++){

                let dayData = {
                    "month": 0,
                    "day": 0,
                }

                if (count == 0){
                    if (!([1,2,3].includes(this.currentDay))){
                        dayData.day = this.currentDay - 3
                        dayData.month = this.currentMonth
                    } else {
                        let lastMonth = this.getLastMonth(this.currentMonth)

                        if (months30.includes(lastMonth)){
                            dayData.day = 27 + this.currentDay
                        } else if (months31.includes(lastMonth)){
                            dayData.day = 28 + this.currentDay
                        } else {
                            dayData.day = 25 + this.currentDay
                        }
                        dayData.month = lastMonth
                    }

                } else {

                    let day = this.visibleBtn[count - 1].day + 1
                    if ([1,2,3].includes(this.currentDay)){
                        let lastMonth = this.getLastMonth(this.currentMonth)

                        if (months30.includes(lastMonth) && day == 31){
                            dayData.day = 1
                        } else if (months31.includes(lastMonth) && day == 32){
                            dayData.day = 1
                        } else if (lastMonth == 1 && day == 29){
                            dayData.day = 1
                        } else {
                            dayData.day = day
                        }
                    
                        if ( dayData.day >= 26){
                            dayData.month = lastMonth
                        } else{
                            dayData.month = this.currentMonth
                        }
                        
                    } else {
                        let thisMonth = this.currentMonth
                        
                        if (months30.includes(thisMonth) && day == 31){
                            dayData.day = 1
                        } else if (months31.includes(thisMonth) && day == 32){
                            dayData.day = 1
                        } else if (thisMonth == 1 && day == 29){
                            dayData.day = 1
                        } else {
                            dayData.day = day
                        }

                        if ( dayData.day >= 4){
                            dayData.month = this.currentMonth
                        } else{
                            dayData.month = this.getNextMonth(this.currentMonth)
                        }

                        if (months30.includes(thisMonth) && this.currentDay > 27){
                            if ( dayData.day >= 4){
                                dayData.month = this.currentMonth
                            } else{
                                dayData.month = this.getNextMonth(this.currentMonth)
                            }
                        } else if (months31.includes(thisMonth) && this.currentDay > 28){
                            if ( dayData.day >= 4){
                                dayData.month = this.currentMonth
                            } else{
                                dayData.month = this.getNextMonth(this.currentMonth)
                            }
                        } else if (thisMonth == 1 && this.currentDay > 25){
                            if ( dayData.day >= 4){
                                dayData.month = this.currentMonth
                            } else{
                                dayData.month = this.getNextMonth(this.currentMonth)
                            }
                        } else {
                            dayData.month = this.currentMonth
                        }
                    }
                    
                    
                }
                this.visibleBtn.push(dayData)
            }
        }
    }
}
</script>

<style>

</style>