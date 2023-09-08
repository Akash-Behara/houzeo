<script setup>
import { Teleport, ref } from 'vue'
import { Carousel, Navigation, Slide } from 'vue3-carousel'
import 'vue3-carousel/dist/carousel.css'
import { MapPinIcon, ListBulletIcon } from "@heroicons/vue/24/outline"


let isShowModal = ref(false)
let currentSlide = ref(0)

function showModal(){
    isShowModal.value = true
    $(document).ready(function(){
        $('#app').on('scroll touchmove mousewheel', function(e){
            e.preventDefault();
            e.stopPropagation();
            return false;
        })
        $('body').css("overflow", "hidden")
    })
}

    function closeModal(){
        isShowModal.value = false
        $(document).ready(function(){
        $('#app').off('scroll touchmove mousewheel');
        $('body').css("overflow", "auto")
    })
    }

    function slideTo(val) {
      currentSlide.value = val
    }

    console.log('s', isShowModal.value)

    const imgArr = [
        "https://t3.ftcdn.net/jpg/01/62/06/40/360_F_162064034_HI2YEgV7km3HMy0rccQczKH2vvpI4OnB.jpg",
        "https://media.istockphoto.com/id/1026205392/photo/beautiful-luxury-home-exterior-at-twilight.jpg?b=1&s=612x612&w=0&k=20&c=FFc1oX54JEIVF4P5613J9Ng7CaN2rmjSU7m1vsnfi1s=",
        "https://images.unsplash.com/photo-1600596542815-ffad4c1539a9?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxzZWFyY2h8OHx8aG91c2V8ZW58MHx8MHx8fDA%3D&w=1000&q=80"
    ]
</script>

<template>
    <div class="image_wrapper">
        <div class="main_img">
            <img :src="imgArr[0]" alt="alt" />
        </div>
        <div class="secondary_img">
            <img :src="imgArr[1]" alt="alt" />
            <img :src="imgArr[2]" alt="alt" />
        </div>
        <div class="more_Photos_container">
            <div class="box"><MapPinIcon class="icon"/>Street View</div>
            <div class="box" @click="showModal"><ListBulletIcon class="icon"/> All Photos ({{imgArr.length}})</div>
        </div>
    </div>
    <Teleport to="#app">
        <dialog class="modal_container" v-if="isShowModal" @click="closeModal">
            <Carousel id="gallery" :items-to-show="1">
                <Slide v-for="img in imgArr" :key="img">
                    <div class="carousel__item"><img :src=img alt="img "/></div>
                </Slide>
            </Carousel>
        </dialog>
    </Teleport>
</template>

<style scoped>

.modal_container{
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    display: flex;
    justify-content: center;
    align-items: center;
    background-color: rgba(0, 0, 0, 0.4);
    -webkit-backdrop-filter: blur(5px);
    backdrop-filter: blur(5px);
    z-index: 999;
}
.image_wrapper{
    display: flex;
    width: 100%;
    background-color: aliceblue;
    gap: 6px;
    position: relative;
}
.main_img{
    flex: 2;
}
.main_img img {
    width: 100%;
    height: 100%;
    object-fit: cover;
    border-radius: 10px 0px 0px 10px;
}
.secondary_img{
    display: flex;
    flex-direction: column;
    gap: 2px;
}
.secondary_img img{
    width: 320px;
    height: 100%;
    border-radius: 0px 10px 10px 0px;
}
.more_Photos_container{
    position: absolute;
    bottom: 5%;
    left: 0;
    width: 100%;
    display: flex;
    justify-content: space-between;
}
.box{
    background-color: white;
    padding: 10px 20px;
    margin: 0px 20px;
    border-radius: 5px;
    border: 2px solid black;
    display: flex;
    align-items: center;
    gap: 6px;
}
.box:hover{
    cursor: pointer;
    scale: 1.01;
    transition: ease-in-out 200ms;
}
.icon{
    width: 20px;
}

@media only screen and (max-width: 1201px){
    .image_wrapper{
        height: 250px;
    }
    .secondary_img img{
        width: 100px;
    }

    .box{
        padding: 2px 5px;
        margin: 0 4px;
    }
}
</style>