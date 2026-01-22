<script setup>
import { ref, reactive, watch } from 'vue'
import { useRoute } from 'vue-router'
import { FooterData } from '../../FooterData.js'

const route = useRoute()
const showAll = ref(false)

const state = reactive({
  list: []
})

const visibleList = () => {
  if (showAll.value) return state.list
  return state.list.slice(0, 11)
}

const clickMore = () => {
  showAll.value = true
}

/* 도움 */
const loadList = () => {
  const found = FooterData.find(
    item => item.path === route.path
  )

  state.list = found ? found.list : []
  showAll.value = false
}

watch(() => route.path, loadList, { immediate: true })

</script>

<template>
<section class="destinations">
  <div class="container">
  <h2 class="title">다음 여행을 위한 추천 여행지</h2>
  <nav class="tabs">
    <router-link
      v-for="item in FooterData"
      :key="item.key"
      :to="item.path"
      class="tab"
      active-class="active"
      @click="showAll = false"
    >
      {{ item.label }}
    </router-link>
  </nav>
  <ul class="list">
    <li v-for="(item, idx) in visibleList()" :key="idx">
      <a
       :href="`https://www.airbnb.co.kr${item.path}`"
        target="_blank"
      >
        <p>{{ item.city }}</p>
        <span>{{ item.desc }}</span>
      </a>
    </li>
    <li v-if="!showAll && state.list.length > 11" class="more">
      <button @click="clickMore">
        더 보기
        <span class="arrow"><svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 384 512"><path d="M169.4 374.6c12.5 12.5 32.8 12.5 45.3 0l160-160c12.5-12.5 12.5-32.8 0-45.3s-32.8-12.5-45.3 0L192 306.7 54.6 169.4c-12.5-12.5-32.8-12.5-45.3 0s-12.5 32.8 0 45.3l160 160z"/></svg></span>
      </button>
    </li>
  </ul>
  </div>
</section>
</template>

<style scoped>
.destinations {
  width: 100%;
  margin: 0;
  padding: 30px 0px;
  background-color: #fafafa;
}

.destinations .title {
  font-size: 22px;
  font-weight: 400;
  margin-bottom: 10px;
}


.tabs {
  display: flex;
  gap: 24px;
  border-bottom: 1px solid #e0e0e0;
  margin-bottom: 32px;
}

.tab {
  position: relative;
  padding: 12px 0;
  font-size: 14px;
  color: #717171;
  text-decoration: none;
  font-weight: 400;
}

.tab.active {
  color: black;
  font-weight: 400;
}

.tab.active::after {
  content: '';
  position: absolute;
  left: 0;
  bottom: -1px;
  width: 100%;
  height: 2px;
  background: black ;
}

.list {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 24px 16px;
  list-style: none;
  padding: 0;
  margin: 0;
}

.list li a {
  display: block;
  text-decoration: none;
  color: inherit;
}

.list li p {
  font-size: 14px;
  font-weight: 400;
  margin: 0 0 2px;
  color: black;
}

.list li span {
  font-size: 13px;
  font-weight: 400;
  color: #717171;
}

.more {
  grid-column: 3 / 4;
}

.more button {
  display: inline-flex;
  align-items: center;
  gap: 6px;
  background: none;
  border: none;
  padding: 0;
  font-size: 14px;
  font-weight: 400;
  color: black;
  cursor: pointer;
}

.more button:hover {
  text-decoration: underline;
}

.more .arrow {
  display: inline-flex;
  width: 12px;
  height: 12px;
}

.more svg {
  width: 100%;
  height: 100%;
  fill: black;
}
</style>