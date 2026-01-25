<script setup>
import HerderMom from './components/header/HerderMom.vue';
import AirbnbInfo from './components/footer/AirbnbInfo.vue';
import LegalInfo from './components/footer/LegalInfo.vue';

</script>

<template>
<HerderMom />
<router-view />
<AirbnbInfo />
<LegalInfo />

</template>

<style scoped>

</style>
