<script setup>
import { socialLinks } from '../../socialLinks.js'
const items = [
      { label: '개인정보 처리방침', path: '/help/article/2855' },
      { label: '쿠키 정책', path: '/help/article/2866' },
      { label: '이용약관', path: '/help/article/2908' },
      { label: '한국의 변경된 환불 정책', path: '/help/article/3837' },
      { label: '회사 세부정보', path: '/about/company-details' }
    ]
</script>

<template>
  <section class="section-1">
    <div class="footer-top">
    <div class="footer-left">
    <div class="copyright">© 2026 Airbnb, inc.</div>
    <ul class="section-list">
      <li v-for="(item, itemIdx) in items" :key="itemIdx">
        <a
          :href="`https://www.airbnb.co.kr${item.path}`"
          target="_blank"
        >
          {{ item.label }}
        </a>
      </li>
    </ul>
    </div>
    <div class="footer-right">
    <button>
        <span><svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 16 16" aria-hidden="true" role="presentation" focusable="false" style="display: block; height: 16px; width: 16px; fill: currentcolor;"><path d="M8 .25a7.77 7.77 0 0 1 7.75 7.78 7.75 7.75 0 0 1-7.52 7.72h-.25A7.75 7.75 0 0 1 .25 8.24v-.25A7.75 7.75 0 0 1 8 .25zm1.95 8.5h-3.9c.15 2.9 1.17 5.34 1.88 5.5H8c.68 0 1.72-2.37 1.93-5.23zm4.26 0h-2.76c-.09 1.96-.53 3.78-1.18 5.08A6.26 6.26 0 0 0 14.17 9zm-9.67 0H1.8a6.26 6.26 0 0 0 3.94 5.08 12.59 12.59 0 0 1-1.16-4.7l-.03-.38zm1.2-6.58-.12.05a6.26 6.26 0 0 0-3.83 5.03h2.75c.09-1.83.48-3.54 1.06-4.81zm2.25-.42c-.7 0-1.78 2.51-1.94 5.5h3.9c-.15-2.9-1.18-5.34-1.89-5.5h-.07zm2.28.43.03.05a12.95 12.95 0 0 1 1.15 5.02h2.75a6.28 6.28 0 0 0-3.93-5.07z"></path></svg></span>
        한국어(KR)
    </button>
    <button>
        <span>₩</span>
        KRW
    </button>
    <div class="social-list">
      <ul >
        <li v-for="item in socialLinks" :key="item.name" class="social-link">
          <a
           :href="item.url"
           target="_blank"
           rel="noopener noreferrer"
            :aria-label="`${item.label}로 이동하기`"
           >
          <span class="icon" v-html="item.svg"></span>
          </a>
        </li>
      </ul>
    </div>
    </div>
    </div>
  </section>
  <section class="footer-text">
    <div class="text">
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
section {
  background-color: #fafafa;
  color: #222;
  font-size: 14px;
}
.section-1{
    padding: 0px 40px ;
}
.footer-text {
    padding: 5px 40px 100px;
}

.footer-top {
  max-width: 1200px;
  margin: 0 auto;
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 25px 0 5px;
  gap: 24px;
  border-top: 1px solid #ddd;
  border-bottom: 1px solid #ddd;
}

.footer-left {
  display: flex;
  flex-wrap: wrap;
  align-items: center;
  gap: 8px 12px;
}

.copyright {
  white-space: nowrap;
}

.section-list {
  display: flex;
  flex-wrap: wrap;
  list-style: none;
  padding: 0;
  margin: 0;
  gap: 8px 12px;
}

.section-list li::before {
  content: "·";
  margin-right: 8px;
  color: #717171;
}

.section-list li:first-child::before {
  content: "";
  margin: 0;
}

.section-list a {
  color: #717171;
  text-decoration: none;
}

.section-list a:hover {
  text-decoration: underline;
}

.footer-right {
  display: flex;
  align-items: center;
  gap: 16px;
  white-space: nowrap;
}

.footer-right button {
  display: flex;
  align-items: center;
  gap: 6px;
  background: transparent;
  border: none;
  padding: 4px;
  font-size: 14px;
  cursor: pointer;
  color: #222;
}


.footer-right svg {
  display: block;
}

.social-list ul {
  display: flex;
  gap: 8px;
  list-style: none;
  padding: 0;
  margin: 0;
}

.social-link {
  width: 36px;
  height: 36px;
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  cursor: pointer;
}

.social-link:hover {
  background-color: #ddd;
}

.icon svg {
  width: 16px;
  height: 16px;
  fill: #222;
}


.footer-text .text {
  max-width: 1200px;
  margin: 0 auto;
  font-size: 12px;
  line-height: 1.5;
  color: #717171;
}

.footer-text .text a {
  color: #717171;
  text-decoration: underline;
}

</style>