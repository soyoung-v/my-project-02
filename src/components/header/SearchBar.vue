<script setup>
import { computed } from 'vue'

const props = defineProps({
  clickTab: String
})

const items = computed(() => {
  switch (props.clickTab) {
    case 'experience':
      return [
        { key: 'location', title: '여행지', desc: '도시나 명소로 검색' },
        { key: 'date', title: '날짜', desc: '날짜 추가' },
        { key: 'guest', title: '여행자', desc: '게스트 추가' },
      ]

    case 'service':
      return [
        { key: 'location', title: '여행지', desc: '여행지 검색' },
        { key: 'date', title: '날짜', desc: '날짜 추가' },
        { key: 'guest', title: '서비스 유형', desc: '서비스 추가' },
      ]

    case 'stay':
    default:
      return [
        { key: 'location', title: '여행지', desc: '여행지 검색' },
        { key: 'date', title: '날짜', desc: '날짜 추가' },
        { key: 'guest', title: '여행자', desc: '게스트 추가' },
      ]
  }
})
</script>

<template>
  <section class="section-2">
  <div class="search-bar event-line">
    <div
      v-for="item in items"
      :key="item.key"
      class="search-item has-line"
    >
      <span class="title">{{ item.title }}</span>
      <span class="desc">{{ item.desc }}</span>
    </div>
  </div>
  <div>
    <button class="search-btn">
      <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 512 512"><path style="fill: white" d="M416 208c0 45.9-14.9 88.3-40 122.7L502.6 457.4c12.5 12.5 12.5 32.8 0 45.3s-32.8 12.5-45.3 0L330.7 376C296.3 401.1 253.9 416 208 416 93.1 416 0 322.9 0 208S93.1 0 208 0 416 93.1 416 208zM208 352a144 144 0 1 0 0-288 144 144 0 1 0 0 288z"/></svg>
    </button>
  </div>
  </section>
</template>

<style scoped>
  .section-2 {
    display: flex;
    justify-content: center;
    align-items: center;
    width: 100%;
    padding: 10px 0 35px 0;
    background-color: #fafafa;
    border-bottom: #DDD 1px solid;
  }
  .search-bar {
  display: flex;
  align-items: center;
  width: 800px;
  height: 66px;
  background: #fff;
  border: #DDD 1px solid;
  border-radius: 999px;
  box-shadow: 0 4px 20px #EBEBEB;
  overflow: hidden;
}

.search-item {
  z-index: 1;
  flex: 1;
  height: 100%;
  border: none;
  background: transparent;
  text-align: left;
  padding: 0 24px;
  cursor: pointer;
  border-radius: 999px;
}

.search-item:hover {
  background: #EBEBEB;
}

.title {
  display: block;
  font-size: 12px;
  color: #222;
  margin-top: 16px;
}

.desc {
  font-size: 14px;
  color: #717171;
  margin-top: 5px;
}

.search-btn {
  position: relative;
  z-index: 2;
  width: 45px;
  height: 45px;
  background: #ff385c;
  border-radius: 50%;
  border: none;
  cursor: pointer;
  left: -60px;
}
.search-btn svg {
  width: 16px;
  height: 16px;
}
.search-btn:hover {
  background: #e61b40;
}

.has-line {
  position: relative;
  padding-left: 24px;
}

.has-line::before {
  content: '';
  position: absolute;
  left: 0;
  top: 50%;
  transform: translateY(-50%);
  width: 1px;
  height: 40px;   
  background-color: #DDD;
}
.event-line:hover .has-line::before {
  opacity: 0;
}

</style>