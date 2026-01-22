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
  <div class="section-inner">
  <div class="title-row">
    <div class="title-left">
      <div class="title_1">{{ item.sectionData.title }}</div>

      <a class="title-arrow" href="#">
        <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 512 512"><path d="M502.6 278.6c12.5-12.5 12.5-32.8 0-45.3l-160-160c-12.5-12.5-32.8-12.5-45.3 0s-12.5 32.8 0 45.3L402.7 224 32 224c-17.7 0-32 14.3-32 32s14.3 32 32 32l370.7 0-105.4 105.4c-12.5 12.5-12.5 32.8 0 45.3s32.8 12.5 45.3 0l160-160z"/></svg>
      </a>
    </div>

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
  <div class="swiper-wrap">
  <Swiper
  slides-per-view="auto"
  :space-between="10"
  :slides-per-group-auto="true"
  :watch-overflow="true"
  :centered-slides="false"
  :navigation="{
    nextEl: `.next-btn-${idx}`,
    prevEl: `.prev-btn-${idx}`,
  }"
  :modules="modules"
    >
      <SwiperSlide
        class="slide"
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
  </div>
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
  width: 29px;
  height: 29px;
  border-radius: 50%;
  background-color: #e8e8ea70;
  display: flex;
  align-items: center;
  justify-content: center;
}

.title-arrow svg {
  width: 11px;
  height: 11px;
  fill: #222222fc;
}
.title_1 { font-size: 1.2rem; font-weight: 150px; }


div.sections { 
  width: auto;
  max-width: 2000px;
  margin-bottom: 40px;
}
div.sections:not(:first-child) { margin-top: 30px; }

.slider-button {
  display: flex;
  gap: 4px;
}

.arrow-btn {
  width: 29px;
  height: 29px;
  border-radius: 50%;
  border: none;
  background: #e8e8ea70;
  display: flex;
  align-items: center;
  justify-content: center;
  cursor: pointer;
  transition: opacity 0.2s ease, background-color 0.2s ease;

}

.arrow-btn svg {
  width: 14px;
  height: 14px;
  fill: #222222ad;
  transition: transform 0.3s ease;
}

.arrow-btn:hover {
  box-shadow: 0 2px 6px rgba(0,0,0,0.15);
  background-color: #DDD;
}
.arrow-btn.swiper-button-disabled {
  opacity: 0.3;
  pointer-events: none; /* 클릭 자체 막기 */
}
.arrow-btn.swiper-button-disabled svg {
  fill: #999;
}
:deep(.swiper-slide) {
   width: 180px !important;
  flex-shrink: 0;
}

.section-inner {
  max-width: calc(
  (185px * 7) + (10px * 6)
  );
  margin: 0 auto;
}
.swiper-wrap {
  width: 100%;
  overflow: hidden;
  padding: 0 16px;
}


@media (max-width: 1440px) {
  .section-inner {
    max-width: calc((185px * 5) + (13px * 4));
  }
}

@media (max-width: 1072px) {
  .section-inner {
    max-width: calc((190px * 4) + (10px * 3));
  }
}

@media (max-width: 887px) {
  .section-inner {
    max-width: calc((190px * 3) + (10px * 2));
  }
}

@media (max-width: 700px) {
  .section-inner {
    max-width: calc((200px * 2) + (10px * 1));
  }
}
@media (min-width: 1887px) {
  .section-inner {
    max-width: calc((245px * 7) + (10px * 6));
  }
  .slide {
    width: 240px !important;
  }
}


</style>