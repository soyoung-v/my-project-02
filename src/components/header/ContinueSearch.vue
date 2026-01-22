<script setup>
import { onMounted, reactive} from 'vue';
import axios from 'axios';

const state = reactive({
  section: null
})

onMounted(async () => {
  axios.get('/airbnb.json')
  .then(res => {state.section = res.data.sections[0]});
});
</script>

<template>
  <section v-if="state.section" class="continue-search">
    <a href="https://www.airbnb.co.kr/s/%EA%B0%95%EB%A6%89%EC%8B%9C/homes?place_id=ChIJWw9PleHlYTURRh09nFHGt4A&refinement_paths%5B%5D=%2Fhomes&checkin=2026-01-16&checkout=2026-01-18&date_picker_type=calendar&adults=1&guests=1" target="_blank">
    <div>{{ state.section.sectionData.searchParams.query }} 숙소 검색 계속하기 <span>{{ state.section.sectionData.items[0].structuredContent.primaryLine[0].body }}</span><span> 게스트 1명</span><span class="right" ><svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 256 512"><path d="M247.1 233.4c12.5 12.5 12.5 32.8 0 45.3l-160 160c-12.5 12.5-32.8 12.5-45.3 0s-12.5-32.8 0-45.3L179.2 256 41.9 118.6c-12.5-12.5-12.5-32.8 0-45.3s32.8-12.5 45.3 0l160 160z"/></svg></span>
    </div></a>
    <div>
      <div class="image-stack">
        <div v-for="(item, idx) in state.section.sectionData.items.slice(0,3)" :key="idx" class="item">
          <img :src="item.contextualPictures[0].picture" :alt="item.title"/>
        </div>
      </div>
    </div>
  </section>
  
</template>

<style scoped>
a { text-decoration: none; color: inherit; }
.right { border: none; border-radius: 25px; width: 20px; height: 20px; 
  background-color: #e8e8ea70; 
  cursor: pointer;
  margin-left: 8px;
  display: inline-flex;
  align-items: center;
  justify-content: center;
}
.right svg { 
  width: 10px;
  height: 10px;
}
span {
  font-size: 14px;
  margin-left: 5px;
  color: #717171;
} 
.continue-search {
  display: flex;
  align-items: center;
  justify-content: center;
  width: 100%;
  border-bottom: 1px solid #DDD ;
  padding: 10px 0;
  cursor: pointer;
}

.image-stack {
  display: flex;
  align-items: center;
  margin-left: 20px;
}

.image-stack img {
  width: 44px;
  height: 44px;
  border-radius: 12px;
  object-fit: cover;
  border : 2px solid #fff;
  box-shadow: 0 2px 6px rgba(0, 0, 0, 0.597);
}

.image-stack .item:nth-child(1) {
  z-index: 3;
}
.image-stack .item:nth-child(2) {
  z-index: 2;
  margin-left: -53px;
  transform: rotate(-8deg);
}
.image-stack .item:nth-child(3) {
  z-index: 1;
  margin-left: -39px;
  transform: rotate(8deg);
}
</style>