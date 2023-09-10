<script setup>
import { ref } from 'vue';
import { useScrollLock } from '@vueuse/core'
import { PlayCircleIcon } from "@heroicons/vue/24/outline"

let peopleArr = [
    {name: "Jared Goldfarb", palce: "Crestone, CO", videoURL: "https://www.youtube.com/embed/G3Tkok_TFvI", thumbNail: "https://images.unsplash.com/photo-1679679008383-6f778fe07828?ixlib=rb-4.0.3&ixid=M3wxMjA3fDF8MHxzZWFyY2h8MXx8cGVvcGxlfGVufDB8fDB8fHww&auto=format&fit=crop&w=500&q=60"},
    {name: "Lori R", palce: "Melbourne, FL", videoURL: "https://www.youtube.com/embed/an5P9uxNc98", thumbNail: "https://images.unsplash.com/photo-1494790108377-be9c29b29330?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxzZWFyY2h8M3x8cGVvcGxlfGVufDB8fDB8fHww&auto=format&fit=crop&w=500&q=60"},
    {name: "Daniel Woodrum", palce: "Panama City Beach, FL", videoURL: "https://www.youtube.com/embed/mpMmOGrdWXY", thumbNail: "https://images.unsplash.com/photo-1539571696357-5a69c17a67c6?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxzZWFyY2h8Nnx8cGVvcGxlfGVufDB8fDB8fHww&auto=format&fit=crop&w=500&q=60"},
    {name: "Ken Marsh", palce: "Williamsburg, VA", videoURL: "https://www.youtube.com/embed/G3Tkok_TFvI", thumbNail: "https://images.unsplash.com/photo-1553530979-fbb9e4aee36f?ixlib=rb-4.0.3&ixid=M3wxMjA3fDF8MHxzZWFyY2h8OHx8cGVvcGxlfGVufDB8fDB8fHww&auto=format&fit=crop&w=500&q=60"},
    {name: "Susan Bish", palce: "Denver, NC", videoURL: "https://www.youtube.com/embed/an5P9uxNc98", thumbNail: "https://plus.unsplash.com/premium_photo-1668399855680-1ee24ade4a29?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxzZWFyY2h8N3x8cGVvcGxlfGVufDB8fDB8fHww&auto=format&fit=crop&w=500&q=60"},
    {name: "Bradon Fletcher", palce: "Cincinnati, OH", videoURL: "https://www.youtube.com/embed/mpMmOGrdWXY", thumbNail: "https://images.unsplash.com/photo-1501196354995-cbb51c65aaea?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxzZWFyY2h8MjJ8fHBlb3BsZXxlbnwwfHwwfHx8MA%3D%3D&auto=format&fit=crop&w=500&q=60"},
]

const isShowModal = ref(false);
const video_url = ref('')

const lockRef = ref<HTMLElement | null>(null)
const isScrollLocked = useScrollLock(lockRef)

let scrolled = ref(window.scrollY)

function closeModal(){
    isShowModal.value = false
    isScrollLocked.value = false
    $(document).ready(function(){
        $('#app').off('scroll touchmove mousewheel');
        $('body').css("overflow", "auto")
    })
}

function showModal(url) {
    isShowModal.value = true
    video_url.value = url
    isScrollLocked.value = true
    console.log('sc', scrolled.value)
    $(document).ready(function(){
        $('#app').on('scroll touchmove mousewheel', function(e){
            e.preventDefault();
            e.stopPropagation();
            return false;
        })
        $('body').css("overflow", "hidden")
    })
}

</script>

<template>
    <div class="people_review_container">
        <h2>Real People, Real Stories</h2>
        <p>See how buyers & sellers across America asre saving on commision using Houzeo technology</p>
        <div class="people_list_container">
            <div v-for="(people, idx) in peopleArr" :key="people.name" class="people_list">
                <div class="people_card">
                    <div class="people_img" @click="showModal(people.videoURL)">
                        <img :src=people.thumbNail alt="people" />
                        <div class="backdrop"></div>
                        <PlayCircleIcon class="play_icon"/>
                    </div>
                    <div class="people_details">
                        <h3>{{people.name}}</h3>
                        <p>{{people.palce}}</p>
                    </div>
                </div>
            </div>
        </div>
    </div>
    <Teleport to="html">
       <div class="modal_container" v-if="isShowModal" @click="closeModal">
            <div class="iframe_container">
                <iframe :src=video_url width="1080" height="480"></iframe>
            </div>
        </div>
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
    z-index: 9999;
}
.people_review_container{
    border: 1px solid #00000026;
    border-radius: 8px;
    padding: 10px 15px;
    margin-top: 20px;
    box-shadow: 2px 2px 2px #58575710;
}
.people_review_container h2{
    font-size: 20px;
    font-weight: 600;
}
.people_review_container p {
    font-size: 14px;
    color: #707070;
    margin-top: 10px;
}
.people_list_container{
    display: flex;
    flex-wrap: wrap;
    gap: 20px;
    margin-top: 20px;
}
.people_list{
    display: flex;
}

.people_card{
    width: 108px;
    border-radius: 6px;
}
.people_img{
    width: 100%;
    height: 71px;
    position: relative;
}

.img_container{
    width: 100%;
    height: 100%;
}
.people_img img {
    width: 100%;
    height: 100%;
    object-fit: cover;
    border-radius: 6px;
}

.backdrop{
    width: 100%;
    height: 100%;
    top: 0;
    left: 0;
    position: absolute;
    background-color: rgba(110, 110, 110, 0.232);
    -webkit-backdrop-filter: blur(0.1px);
    backdrop-filter: blur(0.1px);
}

.play_icon{
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    width: 35px;
    color: white;
}

.people_img:hover{
    cursor: pointer;
    scale: 1.02;
    transition: ease-in-out 200ms ;
}
.people_details{
    margin: 10px;
    transform: translateX(-8px);
}
.people_details h3{
    font-size: 14px;
    font-weight: 600;
}
.people_details p {
    font-size: 10px;
}

</style>