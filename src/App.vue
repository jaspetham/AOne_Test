<script setup>
import { RouterLink, RouterView } from 'vue-router'
import Sidebar from './components/Sidebar.vue';
</script>

<template>
  <main id="main">
    <Sidebar/>
    <RouterView />
  </main>
</template>

<style>
@import '@/assets/base.css';
</style>
