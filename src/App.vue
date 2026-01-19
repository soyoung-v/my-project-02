<script setup>
import TheHeader from './components/header/TheHeader.vue';
import SearchBar from './components/header/SearchBar.vue';
import ContinueSearch from './components/header/ContinueSearch.vue';
import Airbnb from './components/main/Airbnb.vue';
import AirbnbInfo from './components/footer/AirbnbInfo.vue';
import LegalInfo from './components/footer/LegalInfo.vue';

</script>

<template>
<TheHeader />
<SearchBar />
<ContinueSearch />
<Airbnb />
<router-view />
<AirbnbInfo />
<LegalInfo />

</template>

<style scoped>

</style>
