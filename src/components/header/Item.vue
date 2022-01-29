<template >
<div class="item_cont">
    <div class="header_item selected" v-if="isSelected" v-on:click="selectDay(day)">
        <div id="selected_text">{{day.day}} {{fullMonths[day.month]}}</div>
    </div>
    <div class="header_item holiday" v-else-if="isHoliday" v-on:click="selectDay(day)">
        <div class="item_data">{{day.day}}</div>
        <div class="item_data month">{{months[day.month]}}</div>
    </div>
    <div class="header_item" v-else-if="!isSelected"  v-on:click="selectDay(day)">
        <div class="item_data">{{day.day}}</div>
        <div class="item_data month">{{months[day.month]}}</div>
    </div>
</div>
</template>

<script>
export default {
    name: "Item",
    props:{
        day:      Object,
        isSelected: Boolean,
        isHoliday: Boolean,
        selectDay: Function,
    },
    data(){
        return{
            months: ["янв.", "фев.", "март", "апр.", "май", "июнь", "июль", "авг.", "сен.", "окт.", "ноя.", "дек."],
            fullMonths: [
                "января",
                "февраля",
                "марта",
                "апреля",
                "мая",
                "июня",
                "июля",
                "августа",
                "сентября",
                "октября",
                "ноября",
                "декабря"
            ]
        }
    }
}
</script>

<style scoped>
    .item_data{
        width: fit-content;
        margin: 0 auto;
    }
    #selected_text{
        padding-top:7px;
        margin-bottom: auto;
        margin-top: auto;
    }
    .item_cont{
        float: left;
    }
    .item_cont:last-child > .header_item{
        border: 1px solid grey;
    }
    .header_item{
        padding: 8px 1.7vw;
        border: 1px solid grey;
        background: rgb(233, 233, 233);
        width: 5vw;
        min-width: 18.5px;
        height: 4vh;
        text-align: center;
        cursor: pointer;
        border-right: 0px;
        font-size: 14px;
    }
    .header_item div{
        cursor: pointer;
    }
    .selected{
        background: #f7bab7;
        width: 20vw;
        min-width: 75px;
    }
    .holiday{
        background: #F0D2D0;
    }
    .month{
        color: grey;
        font-size: 11px;
    }
</style>