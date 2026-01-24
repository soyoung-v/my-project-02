<script setup>
import { airbnbinfordata } from '../../airbnbinfodata.js'

</script>

<template>
<section class="airbnb-info">
  <div class="container airbnb-grid">
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
</div>
</section>
</template>

<style scoped>
.airbnb-info {
  background-color: #fafafa;
  width: 100%;
  padding: 40px 0px 20px;
}
.airbnb-grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 48px;
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
.airbnb-info > .container {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 48px;
}
@media (max-width: 768px) {
  .airbnb-info {
    grid-template-columns: 1fr;
    gap: 32px;
  }
  .info-section {
    padding: 10px;

  }
}
</style>