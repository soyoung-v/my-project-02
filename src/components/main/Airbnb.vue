<script setup>
import { onMounted, reactive} from 'vue';
import axios from 'axios';
import LodgingItem from './LodgingItem.vue';
import { SwiperSlide, Swiper } from 'swiper/vue';
import 'swiper/css';
import { Navigation } from 'swiper/modules';
const modules = [Navigation]
import 'swiper/css/navigation';

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
  <div
    v-for="(item, idx) in state.sections"
    :key="idx"
    class="sections container"
  >
    <!-- 타이틀 + 버튼 -->
<div class="title-row">
  <!-- 왼쪽: 제목 + 이동 화살표 -->
  <div class="title-left">
    <div class="title_1">{{ item.sectionData.title }}</div>

    <a class="title-arrow" href="#">
      <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 512 512"><!--!Font Awesome Free v7.1.0 by @fontawesome - https://fontawesome.com License - https://fontawesome.com/license/free Copyright 2026 Fonticons, Inc. --><path d="M502.6 278.6c12.5-12.5 12.5-32.8 0-45.3l-160-160c-12.5-12.5-32.8-12.5-45.3 0s-12.5 32.8 0 45.3L402.7 224 32 224c-17.7 0-32 14.3-32 32s14.3 32 32 32l370.7 0-105.4 105.4c-12.5 12.5-12.5 32.8 0 45.3s32.8 12.5 45.3 0l160-160z"/></svg>
    </a>
  </div>

  <!-- 오른쪽: Swiper 버튼 -->
  <div class="slider-button">
    <button :class="`prev-btn-${idx}`" class="arrow-btn">
      <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 256 512">
        <path d="M9.4 233.4c-12.5 12.5-12.5 32.8 0 45.3l160 160c12.5 12.5 32.8 12.5 45.3 0s12.5-32.8 0-45.3L77.3 256 214.6 118.6c12.5-12.5 12.5-32.8 0-45.3s-32.8-12.5-45.3 0l-160 160z"/>
      </svg>
    </button>

    <button :class="`next-btn-${idx}`" class="arrow-btn">
       <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 256 512">
        <path d="M247.1 233.4c12.5 12.5 12.5 32.8 0 45.3l-160 160c-12.5 12.5-32.8 12.5-45.3 0s-12.5-32.8 0-45.3L179.2 256 41.9 118.6c-12.5-12.5-12.5-32.8 0-45.3s32.8-12.5 45.3 0l160 160z"/>
      </svg>
    </button>
  </div>
</div>

    <!-- Swiper -->
    <Swiper
      :slides-per-view="7"
      :space-between="8"
      :navigation="{
        nextEl: `.next-btn-${idx}`,
        prevEl: `.prev-btn-${idx}`,
      }"
      :modules="modules"
      :breakpoints="{
        320: { slidesPerView: 2, spaceBetween: 8 },
        640: { slidesPerView: 3, spaceBetween: 8 },
        1024: { slidesPerView: 5, spaceBetween: 8 },
        1440: { slidesPerView: 7, spaceBetween: 8 }
      }"
    >
      <SwiperSlide
        v-for="subItem in item.sectionData.items"
        :key="subItem.id"
      >
        <LodgingItem
          :picture="subItem.contextualPictures?.[0]?.picture"
          :alt="subItem.title"
          :title="subItem.title"
          :period="subItem.structuredContent?.primaryLine?.[0]?.body"
          :price="subItem.structuredDisplayPrice?.primaryLine?.accessibilityLabel"
          :rating="subItem.avgRatingLocalized"
          :badge="subItem.badges?.length ? subItem.badges[0].text : ''"
        />
      </SwiperSlide>
    </Swiper>
  </div>
</template>

<style scoped>
.title-row {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 12px;
}
.title-left {
  display: flex;
  align-items: center;
  gap: 6px;
}

.title-arrow {
  width: 24px;
  height: 24px;
  border-radius: 50%;
  border: 1px solid #ddd;
  display: flex;
  align-items: center;
  justify-content: center;
}

.title-arrow svg {
  width: 10px;
  height: 10px;
  fill: #222;
}
.title_1 { font-size: 1.2rem; font-weight: 150px; }
.right { border: none; border-radius: 25px; width: 25px; height: 25px; 
  background-color: #e8e8ea70; 
  cursor: pointer;
}
.right svg { 
  width: 10px;
  height: 10px;
}

div.sections { 
  width: auto;
  max-width: 2000px;
  margin-bottom: 40px;
}
div.sections:not(:first-child) { margin-top: 30px; }

.slider-button {
  display: flex;
  gap: 8px;
}

.arrow-btn {
  width: 32px;
  height: 32px;
  border-radius: 50%;
  border: 1px solid #ddd;
  background: white;
  display: flex;
  align-items: center;
  justify-content: center;
  cursor: pointer;
}

.arrow-btn svg {
  width: 12px;
  height: 12px;
  fill: #222;
}

.arrow-btn:hover {
  box-shadow: 0 2px 6px rgba(0,0,0,0.15);
}


</style>