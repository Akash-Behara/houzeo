<script setup>
import { ListBulletIcon, XMarkIcon } from '@heroicons/vue/24/outline'
import { ref } from 'vue';

let showNav = ref(false)
function toggleNav(){
    showNav.value = !showNav.value
    if(showNav.value){
        $(document).ready(function(){
        $('#app').on('scroll touchmove mousewheel', function(e){
            e.preventDefault();
            e.stopPropagation();
            return false;
        })
        $('body').css("overflow", "hidden")
    })
    } else {
        $(document).ready(function(){
        $('#app').off('scroll touchmove mousewheel');
        $('body').css("overflow", "auto")
    })
    }
}
console.log(showNav)
if(window.innerWidth >= 1201){
    showNav.value = true
}
</script>

<template>
    <nav class="mobile_nav_container">
        <div class="mobile_logo_container">
            <div>
                <img src="https://www.houzeo.com/images/new-logo.svg" alt="logo" :width="200" :height="50"/>
            </div>
            <div @click="toggleNav" class="mobile_icon">
                <ListBulletIcon v-if="!showNav" class="icon"/>
                <XMarkIcon v-if="showNav" class="icon"/>
            </div>
        </div>
        <div :class="[showNav ? 'mobile_nav_links_wrapper' : 'mobile_hide']">
            <ul class="mobile_nav_links_container">
                <li>
                    Product
                    <!-- <div class="product_dropdown_container">
                        <select id="product_dropdown">
                            <option class="product_options">Product</option>
                            <option>Product1</option>
                            <option>Product2</option>
                            <option>Product3</option>
                        </select>
                    </div> -->
                </li>
                <li>How Houzeo Works</li>
                <li>Reviews</li>
                <li>Buy</li>
                <li>Sell</li>
                <li>Pricing</li>
                <li>Resources</li>
                <li>Sign In</li>
            </ul>
            <div class="mobile_nav_footer">
                <div class="mobile_contact_details">
                    <span>(844) 448-0110</span>
                    <span>(9am to 6pm CST, Mon-Sat)</span>
                </div>
                <button class="mobile_free_listing_btn">Start Free Listing</button>
            </div>
        </div>
    </nav>
</template>

<style scoped>

@media only screen and (max-width: 1200px)  {
    .mobile_nav_container{
        display: flex;
        justify-content: space-between;
        align-items: center;
        position: relative;
        height: 100px;
        padding: 10px 20px;
        background-color: white;
        z-index: 999;
    }

    .mobile_logo_container{
        display: flex;
        width: 100%;
        justify-content: space-between;
    }

    .mobile_hide{
        display: none;
    }

    .mobile_nav_links_wrapper{
        position: absolute;
        top: 120px;
        left: 0;
        height: 100vh;
        background-color: rgb(43, 43, 42);
        width: 100%;
        display: flex;
        flex-direction: column;
    }

    .mobile_nav_links_container{
        width: 100%;
        list-style: none;
    }
    .mobile_nav_links_container li{
        padding: 15px 10px;
        color: white;
        font-size: 22px;
        cursor: pointer;
    }

    .mobile_nav_footer{
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
    }

    .mobile_contact_details{
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
        width: 100%;
        color: rgb(220, 218, 218);
        margin-top: 20px;
    }

    .mobile_free_listing_btn{
        width: 80%;
        margin-top: 10px;
        padding: 20px 0px;
        font-size: 22px;
        font-weight: 600;
        background: linear-gradient(to right, #2775c0, #0e5294);
        color: white;
    }

    #product_dropdown{
        border: none;
        outline: none;
    }
}

@media only screen and (min-width: 1201px){
    .mobile_icon{
        display: none;
    }
    .mobile_nav_container{
        display: flex;
        justify-content: space-between;
        align-items: center;
        height: 110px;
        z-index: 999;
        padding: 0px 85px;
        background-color: white;
        z-index: 999;
    }

    .mobile_nav_links_wrapper{
        display: flex;
        align-items: center;
    }
    .mobile_nav_links_container{
        display: flex;
        align-items: center;
        list-style: none;
        gap: 20px;
        font-size: 18px;
        font-weight: 600;
    }
    .mobile_nav_footer{
        margin-left: 20px;
        display: flex;
        gap: 20px;
    }
    .mobile_contact_details{
        display: flex;
        flex-direction: column;
        transform: translateY(5px);
    }
    .mobile_free_listing_btn{
        padding: 10px 20px;
        font-size: 22px;
        font-weight: 600;
        border: none;
        border-radius: 5px;
        margin-right: 15px;
        background: linear-gradient(to right, #2775c0, #0e5294);
        color: white;
    }
}

.icon{
    width: 40px;
    cursor: pointer;
}



</style>