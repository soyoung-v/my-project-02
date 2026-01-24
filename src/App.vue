<script setup>
import { ref } from 'vue'
const clickTab = ref('stay')

import TheHeader from './components/header/TheHeader.vue';
import SearchBar from './components/header/SearchBar.vue';
import ContinueSearch from './components/header/ContinueSearch.vue';
import Airbnb from './components/main/Airbnb.vue';
import AirbnbInfo from './components/footer/AirbnbInfo.vue';
import LegalInfo from './components/footer/LegalInfo.vue';

</script>

<template>
  <p>clickTab: {{ clickTab }}</p>
<TheHeader     
  :clickTab="clickTab"
  @change-tab="clickTab = $event"
/>
<SearchBar :clickTab="clickTab" />
<ContinueSearch v-if="clickTab === 'stay'" />
<Airbnb :clickTab="clickTab" />
<router-view />
<AirbnbInfo />
<LegalInfo />

</template>

<style scoped>

</style>
