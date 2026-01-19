<script setup>
import { airbnbinfordata } from '../../airbnbinfodata.js'

</script>

<template>
<section class="airbnb-info">
  <div v-for="(section, idx) in airbnbinfordata" :key="idx" class="info-section">
    <h3 class="section-title">{{ section.title }}</h3>
    <ul class="section-list">
      <li v-for="(item, itemIdx) in section.items" :key="itemIdx">
        <a
          :href="item.path2 ? item.path2 : `https://www.airbnb.co.kr${item.path}`"
          target="_blank"
        >
          {{ item.label }}
        </a>
      </li>
    </ul>
  </div>
</section>
</template>

<style scoped>
.airbnb-info {
  border-bottom: 1px solid #dddddd;
  background-color: #fafafa;
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 48px;
  max-width: 1120px;
  margin: 0 auto;
  padding: 40px 30px 20px;
}
.section-title {
  font-size: 14px;
  font-weight: 400;
  color: black;
  margin-bottom: 16px;
}
.section-list {
  list-style: none;
  padding: 0;
  margin: 0;
}
.section-list li {
  margin-bottom: 17px;
}
.section-list a {
  font-size: 14px;
  line-height: 18px;
  color: #717171;
  text-decoration: none;
}

.section-list a:hover {
  text-decoration: underline;
  color: black;
}
@media (max-width: 768px) {
  .airbnb-info {
    grid-template-columns: 1fr;
    gap: 32px;
  }
  .info-section {
    padding: 10px;
    border-bottom: 1px solid #dddddd;
  }
}
</style>