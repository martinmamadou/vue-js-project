<script setup>
import HomeView from './views/HomeView.vue';
import FooterComp from './components/FooterComp.vue'
import HeaderComp from './components/HeaderComp.vue'
import {RouterView } from 'vue-router'
</script>

<template>
    <HeaderComp />
    <RouterView />
    <FooterComp />
</template>

<style scoped>

</style>
