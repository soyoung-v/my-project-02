<script setup>
import { ref, onMounted, onUnmounted } from 'vue'

import TheHeader from './TheHeader.vue'
import SearchBar from './SearchBar.vue'
import ContinueSearch from './ContinueSearch.vue'
import Airbnb from '../main/Airbnb.vue'

const clickTab = ref('stay')
const isSticky = ref(false)

const onScroll = () => {
  isSticky.value = window.scrollY > 1
}

onMounted(() => window.addEventListener('scroll', onScroll))
onUnmounted(() => window.removeEventListener('scroll', onScroll))
</script>

<template>
  <div class="header-mom">
  <TheHeader
    :clickTab="clickTab"
    :isSticky="isSticky"
    @change-tab="clickTab = $event"
  /></div>
  <SearchBar v-if="!isSticky" :clickTab="clickTab" />
  <ContinueSearch v-if="clickTab === 'stay'" />
  <Airbnb :clickTab="clickTab" />
</template>

<style scoped>
.header-mom {
  position: sticky;
  top: 0;
  z-index: 1000;
  background-color: #fafafa;
}
</style>