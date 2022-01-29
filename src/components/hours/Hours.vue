<template>
    <div id="vue_calendar_hours">
        <div
            v-for="n in workHours"
            :key="n"
            class="hour_cont"
        >
            <div class="line_cont">
                <hr class="big_line" color="lightskyblue" size="1.6px">
            </div>
            <div class="hour">{{n}}:00</div>
            <div class="line_cont">
                <hr class="small_line" color="lightskyblue" size="1.6px">
            </div>
        </div>
    </div>
</template>

<script>
export default {
    name: "Hours",
    props: {
        workHours: Array,
    }
}
</script>

<style scoped>
.hour_cont{
    height: calc(4vh + 17px);
    width: 35px;
}
.hour{
    font-size:11px;
    margin-top: 4px;
    margin-bottom: 4px;
    color: rgb(143, 143, 143);
}

.big_line{
    width: 15px;
    margin: 2px 0px;
    float: right;
}
.small_line{
    width: 8px;
    margin: 2px 0px;
    float: right;
}
.line_cont{
    height: 3px;
    margin-right: 4px;
}
</style>