<script setup>
import Posts from './components/Posts.vue'
import Posts2 from './components/Posts2.vue';
import * as Vue from 'vue'
import axios from 'axios'
import VueAxios from 'vue-axios'
import Sidebar from './components/Sidebar.vue'
import MainContent from './components/MainContent.vue';
</script>

<template>
  <main id="main">
    <Sidebar/>
    <MainContent/>
  </main>
</template>

<style>
@import './assets/base.css';
#app{
  width:100%;
  height: 100%;
}

</style>
