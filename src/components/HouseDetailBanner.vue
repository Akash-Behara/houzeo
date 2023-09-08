<script setup>
import { CurrencyDollarIcon } from "@heroicons/vue/24/outline"

</script>

<template>
    <div class="house_banner_wrapper">
        <div class="house_address">
            <h2>2856 Meadow Park Ave,</h2>
            <p>Henderson, NV 89052</p>
        </div>
        <div class="house_details">
            <div class="house_cost">
                <h2>$500,000</h2>
                <p>Est. $4,284/mo <span class="get_approved"><CurrencyDollarIcon class="currency_icon"/>Get Pre-Approved</span></p>
            </div>
            <div class="house_area">
                <div class="">
                    <h2>4</h2>
                    <p>Beds</p>
                </div>
                <div>
                    <h2>3</h2>
                    <p>Bath</p>
                </div>
                <div>
                    <h2>998</h2>
                    <p>sq.ft</p>
                </div>
            </div>
            <div class="offer">
                <button>Make an Offer</button>
            </div>
        </div>
    </div>
</template>

<style scoped>
@media only screen and (max-width: 1201px){
    .house_banner_wrapper{
        display: flex;
        flex-direction: column;
    }
}
.house_banner_wrapper{
    height: 100%;
    background-color: white;
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 10px 100px;
    border-top: 1px solid lightgray;
    box-shadow: 2px 4px 4px #909090;
    border-radius: 0px 0px 6px 6px;
    z-index: 999;
}
.house_details{
    display: flex;
    align-items: center;
    gap: 40px;
}
.house_cost{
    line-height: .4;
}
.house_cost h2{
    font-weight: 800;
}
.house_cost p{
    font-size: 16px;
}
.get_approved{
    margin-left: 10px;
    color: #115ea7;
    font-weight: 700;
}

.currency_icon{
    width: 25px;
    transform: translateY(7px);
}

.house_area{
    display: flex;
    margin-left: 20px;
    line-height: .4;
    gap: 30px;
}
.offer button{
    border: none;
    padding: 15px 25px;
    height: 100%;
    background-color: #f15d28;
    color: white;
    font-size: 22px;
    border-radius: 6px;
    font-weight: 600;
    cursor: pointer;
}
</style>