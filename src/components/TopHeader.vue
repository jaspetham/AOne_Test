<script setup>
    defineProps({
      title: {
        type: String,
        required: true
      }
    })
</script>

<template>
    <div class="top-header flex justify-between">
        <h1 class="fs-600 font-bold">{{title}}</h1>
        <div class="user flex gap-x-3 items-center">
            <span class="fs-400 font-semibold">Jones Ferdinand</span>    
            <div class="user-img">
                <img src="/assets/user.png" alt="user">
            </div>
        </div> 
    </div>
</template>

<style scoped>
    .user-img{
        border-radius:50%;
        border:2px solid white;
        display:flex;
        align-content: center;
        justify-content: center;
        box-shadow: 0px 0px 5px 5px rgba(0,0,0,0.1);
    }
    .user-img > img{
        border-radius: 50%;
    }
</style>