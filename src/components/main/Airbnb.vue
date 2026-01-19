<script setup>
import { onMounted, reactive} from 'vue';
import axios from 'axios';
import LodgingItem from './LodgingItem.vue';

const state = reactive({
  sections : []
});

onMounted(async () => {
  axios.get('/airbnb.json')
  .then(res => {state.sections = res.data.sections
    console.log(state.sections)});
});

</script>

<template>
    <div v-for="(item, idx) in state.sections" :key="idx" class="sections">
        <div class="title_1">{{ item.sectionData.title }} <button class="right" href="#"><svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 512 512"><!--!Font Awesome Free v7.1.0 by @fontawesome - https://fontawesome.com License - https://fontawesome.com/license/free Copyright 2026 Fonticons, Inc. --><path d="M502.6 278.6c12.5-12.5 12.5-32.8 0-45.3l-160-160c-12.5-12.5-32.8-12.5-45.3 0s-12.5 32.8 0 45.3L402.7 224 32 224c-17.7 0-32 14.3-32 32s14.3 32 32 32l370.7 0-105.4 105.4c-12.5 12.5-12.5 32.8 0 45.3s32.8 12.5 45.3 0l160-160z"/></svg></button>
        </div>
          <div class="d-flex">
          <LodgingItem v-for="subItem in item.sectionData.items" :key="subItem.demandStayListing.id"
            :picture="subItem.contextualPictures[0].picture"
            :alt="subItem.title"
            :title="subItem.title"
            :period="subItem.structuredContent.primaryLine[0].body"
            :price="subItem.structuredDisplayPrice.primaryLine.accessibilityLabel"
            :rating="subItem.avgRatingLocalized"
            :badge="subItem.badges.length ? subItem.badges[0].text: ''"
          />
        </div>
    </div>
</template>

<style scoped>
.d-flex { display: flex; overflow-x: scroll; }
.title_1 { font-size: 1.2rem; font-weight: 150px; margin-bottom: 15px; }
.right { border: none; border-radius: 25px; width: 25px; height: 25px; 
  background-color: #e8e8ea70; 
  cursor: pointer;
}
.right svg { 
  width: 10px;
  height: 10px;
}

div.sections { width: 100%; }
div.sections:not(:first-child) { margin-top: 30px; }
</style>