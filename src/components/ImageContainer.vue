<script setup>
import { Teleport, ref } from 'vue'
import 'vue3-carousel/dist/carousel.css'
import { MapPinIcon, ListBulletIcon, ArrowLeftIcon, ArrowLeftCircleIcon, ArrowRightCircleIcon } from "@heroicons/vue/24/outline"

const imgArr = [
    "https://t3.ftcdn.net/jpg/01/62/06/40/360_F_162064034_HI2YEgV7km3HMy0rccQczKH2vvpI4OnB.jpg",
    "https://media.istockphoto.com/id/1026205392/photo/beautiful-luxury-home-exterior-at-twilight.jpg?b=1&s=612x612&w=0&k=20&c=FFc1oX54JEIVF4P5613J9Ng7CaN2rmjSU7m1vsnfi1s=",
    "https://images.unsplash.com/photo-1600596542815-ffad4c1539a9?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxzZWFyY2h8OHx8aG91c2V8ZW58MHx8MHx8fDA%3D&w=1000&q=80"
]

    let isShowModal = ref(false)
    let currentSlide = ref(0)
    let windowScrollY = ref(0)
    let imgCount = ref(1)

    $(document).ready(function(){
        $(window).on('scroll', function(e) {
            windowScrollY.value = window.scrollY
        });
        $('#modal_container').css({'height':  '' })
    })
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

    function prev_img(){
        if(imgCount.value == 1) return
        imgCount.value = imgCount.value - 1
    }
    function next_img(){
        if(imgArr.length == imgCount.value) return
        imgCount.value = imgCount.value + 1
    }
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
        <dialog class="modal_container" id="modal_container" v-if="isShowModal">
            <div class="wrapper">
                <div class="img_count">
                    <div class="arrow_left_icon"><ArrowLeftIcon @click="closeModal"/></div>
                    <div>{{imgCount}} of {{imgArr.length}}</div>
                    <div class="make_offer_txt">Make an Offer <p class="underline"></p></div>
                </div>
                <div class="img_modal">
                    <div @click="prev_img" class="next_img_btn"><ArrowLeftCircleIcon /></div>
                    <img :src="imgArr[imgCount -1]" alt="img" />
                    <div @click="next_img" class="next_img_btn"><ArrowRightCircleIcon /></div>
                </div>
            </div>
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
    background-color: rgba(0, 0, 0, 0.4);
    -webkit-backdrop-filter: blur(5px);
    backdrop-filter: blur(5px);
    z-index: 999;
}
.wrapper{
    background-color: white;
    width: 100%;
    height: 100%;
    background-color: rgba(0, 0, 0, 0.4);
    -webkit-backdrop-filter: blur(5px);
    backdrop-filter: blur(5px);
}
.img_count{
    color: white;
    display: flex;
    justify-content: space-between;
    margin-top: 40px;
    padding: 0px 100px;
}
.img_modal{
    width: 100%;
    height: 100%;
    display: flex;
    justify-content: center;
    align-items: center;
    transform: translate(-20px, -50px);
}
.img_modal img {
    width: 50%;
    border-radius: 8px;
}
.underline{
    border: 1px solid white;
}
.make_offer_txt{
    z-index: 99;
    cursor: pointer;
}
.arrow_left_icon{
    width: 30px;
    z-index: 99;
    cursor: pointer;
}
.arrow_left_icon:hover{
    scale: 1.04;
    transition: ease-in-out 200ms;
}
.next_img_btn{
    color: rgba(255, 255, 255, 0.46);
    width: 30px;
    z-index: 99;
    margin: 0px 10px;
    cursor: pointer;
}
.next_img_btn:hover{
    color: white;
    scale: 1.04;
    transition: ease-in-out 200ms;
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
    padding: 5px 8px;
    margin: 0px 20px;
    border-radius: 5px;
    border: 2px solid black;
    display: flex;
    align-items: center;
    gap: 6px;
    font-size: 16px;
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
        height: 380px
    }
    .secondary_img img{
        width: 200px;
    }

    .box{
        padding: 2px 5px;
        margin: 0 4px;
    }
}
@media only screen and (max-width: 768px){
    .image_wrapper{
        height: 200px
    }
    .secondary_img img{
        width: 120px;
    }
    .img_count{
        padding: 0px 10px;
    }
    .img_modal{
        transform: translate(0, -100px);
    }
    .img_modal img {
        width: 80%;
    }
}
</style>