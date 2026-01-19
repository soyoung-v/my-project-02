<script setup>

</script>

<template>
  <section>
    <div>© 2026 Airbnb, inc.</div>
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
    <button>
        <span class="arrow"><svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 384 512"><path d="M169.4 374.6c12.5 12.5 32.8 12.5 45.3 0l160-160c12.5-12.5 12.5-32.8 0-45.3s-32.8-12.5-45.3 0L192 306.7 54.6 169.4c-12.5-12.5-32.8-12.5-45.3 0s-12.5 32.8 0 45.3l160 160z"/></svg></span>
        한국어(KR)
    </button>
    <button>
        <span class="arrow"><svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 384 512"><path d="M169.4 374.6c12.5 12.5 32.8 12.5 45.3 0l160-160c12.5-12.5 12.5-32.8 0-45.3s-32.8-12.5-45.3 0L192 306.7 54.6 169.4c-12.5-12.5-32.8-12.5-45.3 0s-12.5 32.8 0 45.3l160 160z"/></svg></span>
        KRW
    </button>
    <div class="btn-wrap">
      <button v-for="(btn,idx) in btns" :key="idx" class="btn"><svg xmlns="http://www.w3.org/2000/svg" :viewBox="btn.viewBox"><path :d="btn.d"/></svg></button>
    </div>
    <div>
      웹사이트 제공자: Airbnb Ireland UC, private unlimited company, 8 Hanover Quay Dublin 2,
      D02 DP23 Ireland | 이사: Dermot Clarke, Killian Pattwell, Andrea Finnegan | VAT 번호:
      IE9827384L | 사업자 등록 번호: IE 511825 | 연락처: terms@airbnb.com, 웹사이트,
      080-822-0230 | 호스팅 서비스 제공업체: 아마존 웹서비스 | 에어비앤비는 통신판매 중개자로
      에어비앤비 플랫폼을 통하여 게스트와 호스트 사이에 이루어지는 통신판매의 당사자가 아닙니다.
      에어비앤비 플랫폼을 통하여 예약된 숙소, 체험, 호스트 서비스에 관한 의무와 책임은 해당
      서비스를 제공하는 호스트에게 있습니다.
    </div>
  </section>
</template>

<style scoped>

</style>