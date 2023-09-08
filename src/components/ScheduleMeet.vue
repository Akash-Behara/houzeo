<script setup>

import { Carousel, Navigation, Slide } from 'vue3-carousel'

import 'vue3-carousel/dist/carousel.css'
import PeopleReview from './PeopleReview.vue';
import { ref } from 'vue';

let session = ref(true)

function toggleSession(val){
    session.value = val
}

var getDaysOfMonth = function(year, month) {
    var monthDate = moment(year+'-'+month, 'YYYY-MM');
    var daysInMonth = monthDate.daysInMonth();
    var arrDays = [];

    while(daysInMonth) { 
        var current = moment().date(daysInMonth);
        arrDays.unshift({day: current.format('ddd'), date: current.format('DD'), month: current.format('MMM')});
        daysInMonth--;
    }
    return arrDays;
};
var dateList = getDaysOfMonth(2023, 9);

const generateHoursInterval = (
  startHourInMinute,
  endHourInMinute,
  interval,
) => {
  const times = [];

  for (let i = 0; startHourInMinute < 24 * 60; i++) {
    if (startHourInMinute > endHourInMinute) break;

    var hh = Math.floor(startHourInMinute / 60);
    var mm = startHourInMinute % 60;
    times[i] = ('0' + (hh % 24)).slice(-2) + ':' + ('0' + mm).slice(-2);
    startHourInMinute = startHourInMinute + interval;
  }
  return times;
};

const interval = 30;
const startDate = 60 * 9;
const endDate = 60 * 17; 
const foo = generateHoursInterval(startDate, endDate, interval);

</script>

<template>
    <div class="">
        <div class="schedule_container">
            <h2>Schedule a Showing</h2>
            <div class="toggle_session">
                <div @click="toggleSession(true)" class="active">In person showing</div>
                <div @click="toggleSession(false)">Virtual showing</div>
            </div>
            <div class="date_slider">
                <Carousel class="dates_slider_slick" :items-to-show="5" :items-to-scroll="2">
                    <Slide v-for="(day, idx) in dateList" :key="idx">
                        <div class="day_card"><div class="day">{{day.day}}</div> <div class="date">{{ day.date }}</div> <div class="month">{{day.month}}</div></div>
                    </Slide>
                    <template #addons>
                        <Navigation />
                    </template>
                </Carousel>
            </div>
            <div class="time_slider">
                <Carousel class="time_slider_slick" :items-to-show="6" :items-to-scroll="2">
                    <Slide v-for="(time, idx) in foo" :key="idx">
                        <div class="time_card">{{time}}</div>
                    </Slide>
                    <template #addons>
                        <Navigation />
                    </template>
                </Carousel>
            </div>
            <div class="schedule_btn_container">
                <button>Schedule Showing</button>
            </div>
            <p class="schdeule_cancel_txt">Its free with no obligation - cancel anytime All times in EDT</p>
        </div>

        <div>
            <PeopleReview />
        </div>
    </div>
</template>

<style scoped>
.schedule_container{
    border: 1px solid lightgray;
    padding: 10px;
    border-radius: 5px;
}
.toggle_session{
    display: flex;
    background-color: lightgray;
    padding: 5px;
    height: 40px;
    border-radius: 5px;
    display: flex;
    justify-content: space-around;
    align-items: center;
    font-weight: 700;
}
.toggle_session .active{
    width: 50%;
    height: 100%;
    font-weight: 700;
    display: flex;
    justify-content: center;
    align-items: center;
    background-color: white;
}

.dates_slider_slick{
    display: flex;
}

.time_slider_slick{
    display: flex;
}

.time_slider{
    margin-top: 10px;
}

.day_card{
    height: 110px;
    width: 100px;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    border-radius: 8px;
    padding: 10px 15px;
    margin: 0px 5px;
    border: 1px solid lightgray
}

.day_card:hover{
    cursor: pointer;
}

.day{
    font-size: 17px;
}

.date{
    font-size: 32px;
    font-weight: 600;
    margin: 2px 0px
}
.date_slider{
    margin-top: 10px;
}

.time_card{
    border: 1px solid lightgray;
    padding: 8px 12px;
    border-radius: 5px;
}

.time_card:hover{
    cursor: pointer;
}

.schedule_btn_container{
    display: flex;
    justify-content: center;
    align-items: center;
    margin-top: 20px;
}

.schedule_btn_container button{
    padding: 12px 0px;
    border: none;
    font-size: 24px;
    width: 100%;
    color: white;
    border-radius: 5px;
    background: linear-gradient(to right, #2775C0, #0F5395);
    cursor: pointer;
}

.schdeule_cancel_txt{
    margin-top: 20px;
    color: rgb(138, 138, 138);

}

</style>