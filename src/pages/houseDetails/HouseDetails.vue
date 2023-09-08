<script setup>
import ImageContainer from '../../components/ImageContainer.vue'
import ScheduleMeet from '../../components/ScheduleMeet.vue'

import { EyeIcon, HeartIcon } from "@heroicons/vue/24/outline"


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
            <hr />
            <div class="description_container">
                <h2>Description</h2>
                <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Odit optio facilis quae, fuga laboriosam mollitia facere laudantium incidunt dicta? Dolore consectetur debitis reprehenderit beatae dignissimos et nisi accusamus, ullam amet?</p>
            </div>
            <hr />
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
    padding: 10px 100px;
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
    height: 45px;
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
    font-size: 16px;
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
    height: 20px;
    width: 20px;
    background-color: green;
    border-radius: 5px;
}

.status_wrapper p {
    font-size: 18px;
    color: #393838;
    font-weight: 600;
}

.description_container h2{
    font-size: 30px;
    font-weight: 700;
}
.description_container p {
    font-size: 1.3rem;
}

.property_detail_container h2{
    font-size: 30px;
    font-weight: 700;
}

table{
    border-spacing: 0;
}

.table_col{
    background-color:aliceblue;
    width: 50%;
    padding: 10px;
    font-weight: 600;
    font-size: 1.2rem;
}
.table_col_value{
    padding-left: 30px;
    font-size: 1.2rem;
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