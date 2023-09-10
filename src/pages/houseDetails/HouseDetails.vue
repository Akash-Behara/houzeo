<script setup>
import { ref } from 'vue';
import ImageContainer from '../../components/ImageContainer.vue'
import ScheduleMeet from '../../components/ScheduleMeet.vue'

import { EyeIcon, HeartIcon, ArrowDownIcon } from "@heroicons/vue/24/outline"

let continueReading = ref(false)

function toggleContinueReading(){
    continueReading.value = !continueReading.value
}


</script>

<template>
    <div class="house_detail_container" id="modal">
        <div class="desciption_container">
            <div>
                <ImageContainer />
            </div>
            <div class="view_wrapper">
                <div class="view_container">
                    <div class="view_box"><EyeIcon class="icon"/>2.3K</div>
                    <div class="view_box"><HeartIcon class="icon"/>2.3K</div>
                </div>
                <div class="status_wrapper">
                    <div class="status"></div>
                    <p>For Sale</p>
                </div>
            </div>
            <div class="divider"></div>
            <div class="description_container">
                <h2>Description</h2>
                <p>Welcome home to this beautiful center hall Colonial located in desirable North Caldwell! This house is the epitome of old-world charm meets modern-day living. The first floor boasts an open floorplan, including a welcoming foyer and a spacious living room for entertaining. The eat-in kitchen exudes modern elegance with a marble backsplash, white cabinetry
                    <span class="continue_reading_txt" @click="toggleContinueReading" v-if="!continueReading">...Continue Reading <ArrowDownIcon class="icon" /></span>
                    <span v-if="continueReading">Lorem ipsum dolor sit amet consectetur adipisicing elit. Adipisci consequatur, vitae veniam numquam modi laborum nostrum recusandae, aspernatur nam voluptate amet officia rem blanditiis voluptatibus quia natus, accusantium facilis debitis.</span>
                </p>
            </div>
            <div class="divider"></div>
            <div class="property_detail_container">
                <h2>Property Details</h2>
                <div>
                    <table>
                        <tr>
                            <td class="table_col">Type</td>
                            <td class="table_col_value">Single Family</td>
                        </tr>
                        <tr>
                            <td class="table_col">Status</td>
                            <td class="table_col_value">Active</td>
                        </tr>
                        <tr>
                            <td class="table_col">Days on Market</td>
                            <td class="table_col_value">5</td>
                        </tr>
                        <tr>
                            <td class="table_col">Open House</td>
                            <td class="table_col_value">Not Scheduled</td>
                        </tr>
                        <tr>
                            <td class="table_col">Country</td>
                            <td class="table_col_value">Lincoln</td>
                        </tr>
                        <tr>
                            <td class="table_col">MLS Name</td>
                            <td class="table_col_value">Montana Regional MLS</td>
                        </tr>
                        <tr>
                            <td class="table_col">MLS Number</td>
                            <td class="table_col_value">22208962</td>
                        </tr>
                        <div :style="{heigth: '1px', width: '100%'}"></div>
                        <tr>
                            <td class="table_col">Year Built</td>
                            <td class="table_col_value">2002</td>
                        </tr>
                        <tr>
                            <td class="table_col">Finished Area</td>
                            <td class="table_col_value">1,837 sq.ft</td>
                        </tr>
                        <tr>
                            <td class="table_col">Lot Size</td>
                            <td class="table_col_value">0.18 acres</td>
                        </tr>
                        <tr>
                            <td class="table_col">Basement</td>
                            <td class="table_col_value">600 sq.ft</td>
                        </tr>
                        <tr>
                            <td class="table_col">No. of Stories</td>
                            <td class="table_col_value">2</td>
                        </tr>
                        <tr>
                            <td class="table_col">HOA Fees</td>
                            <td class="table_col_value">$110</td>
                        </tr>
                        <tr>
                            <td class="table_col">Buyer Agent Commision</td>
                            <td class="table_col_value">2%</td>
                        </tr>
                    </table>
                </div>
            </div>
        </div>
        <div class="schedule_container">
            <ScheduleMeet />
        </div>
    </div>
</template>


<style scoped>
.house_detail_container{
    display: flex;
    padding: 10px 85px;
    gap: 30px;
}
.desciption_container{
    width: 70%;
}
.schedule_container{
    width: 30%;
}
.view_wrapper{
    display: flex;
    justify-content: space-between;
    margin-top: 20px;
    height: 35px;
}

.view_container {
    display: flex;
    gap: 20px;
}

.view_box{
    background-color: lightgray;
    display: flex;
    justify-content: center;
    align-items: center;
    padding: 0px 14px;
    border-radius: 5px;
    font-weight: 600;
    font-size: 14px;
}

.icon{
    width: 24px;
    margin-right: 5px;
}

.status_wrapper{
    display: flex;
    align-items: center;
    gap: 10px;
}
.status{
    height: 16px;
    width: 16px;
    background-color: #00B67B;
    border-radius: 5px;
}

.status_wrapper p {
    font-size: 16px;
    color: #393838;
    font-weight: 600;
    opacity: 0.8;
}

.divider{
    margin: 20px 0px;
    border: 1px solid #3d3d3d20;
    height: 1px;
}
.description_container h2{
    font-size: 20px;
    font-weight: 600;
}
.description_container p {
    font-size: 16px;
    margin-top: 10px;
}

.property_detail_container h2{
    font-size: 20px;
    font-weight: 600;
}

table{
    border-spacing: 0;
    margin-top: 20px;
}

.table_col{
    background-color:aliceblue;
    width: 50%;
    padding: 10px;
    font-weight: 600;
    font-size: 16px;
}
.table_col_value{
    padding-left: 30px;
    font-size: 16px;
}
.continue_reading_txt{
    text-decoration: underline;
    font-weight: 600;
    cursor: pointer;
}
.continue_reading_txt .icon{
    width: 16px;
    font-weight: 600;
    transform: translateY(2px);
}

@media only screen and (max-width: 1201px){
    .house_detail_container{
        display: flex;
        flex-direction: column;
        padding: 10px 20px
    }

    .desciption_container{
        width: 100%
    }

    .schedule_container{
        width: 100%;
    }
}
</style>