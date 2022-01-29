<template>
    <div class="vue_calendar_column">
        <div v-if="!selected">
            <div
                v-for="hour in workHours"
                :key="hour"
                class="table_item" 
            ></div>
        </div>
        <div v-if="selected">
            <div
                v-for="hour in workHours"
                :key="hour"
                class="table_item selected" 
            ></div>
        </div>
    </div>
</template>

<script>
export default {
    name: "Table",
    props: {
        workHours: Array,
        selected: Boolean,
    }
}
</script>

<style scoped>
.table_item{
    padding: 8px 1.7vw;
    border: 1px solid grey;
    width: 5vw;
    min-width: 18.5px;
    height: 4vh;
    cursor: pointer;
    border-top: 0;
    border-right: 0;
}
.selected{
    width: 20vw;
    min-width: 75px;
}

.vue_calendar_column{
    float: left;
}

.vue_calendar_column:last-child > div > .table_item{
    border-right: 1px solid grey;
}

</style>