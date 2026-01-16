<script setup>
import { ref } from 'vue'

defineProps({
  msg: String,
})

const count = ref(0)
</script>

<template>

<footer>
<section>
  <h2>다음 여행을 위한 추천 여행지</h2>
  <div>
    <button>인기</button>
    <button>예술 및 문화</button>
    <button>해변</button> 
    <button>산맥</button> 
    <button>야외</button> 
    <button>즐길거리</button> 
  </div>
  <div>
    <ul>
      <li><a href=""><span>클리블랜드</span><br>장기 숙소</a></li>
      <li><a href=""><span>필라델피아</span><br>아파트 숙소</a></li>
      <li><a href=""><span>걸프 쇼어스</span><br>저택 숙소</a></li>
      <li><a href=""><span>몬트리올</span><br>휴가지 숙소</a></li>
      <li><a href=""><span>도쿄</span><br>콘도 숙소</a></li>
      <li><a href=""><span>찰스턴</span><br>아파트 숙소</a></li>
      <li><a href=""><span>교토시</span><br>아파트 숙소</a></li>
    </ul>
  </div>
  
  <button><span>더보기</span></button>
</section>

<section>
  <h3>에어비앤비 지원</h3>
  <div>
  <ul>
    <li><a href="">도움말 센터</a></li>
    <li><a href="">안전 문제 관련 도움받기</a></li>
    <li><a href="">에어커버</a></li>
    <li><a href="">차멸 반대</a></li>
    <li><a href="">장애인 지원</a></li>
    <li><a href="">예약 취소 옵션</a></li>
    <li><a href="">이웃 민원 신고</a></li>
  </ul>
  </div>
</section>

<section>
    <h3>호스팅</h3>
  <div>
  <ul>
    <li><a href="">도움말 센터</a></li>
    <li><a href="">안전 문제 관련 도움받기</a></li>
    <li><a href="">에어커버</a></li>
    <li><a href="">차멸 반대</a></li>
    <li><a href="">장애인 지원</a></li>
    <li><a href="">예약 취소 옵션</a></li>
    <li><a href="">이웃 민원 신고</a></li>
  </ul>
  </div>
</section> 

<section>
  <h3>에어비앤비</h3>
  <div>
    <ul>
    <li><a href="">2025 여름 업그레이드</a></li>
    <li><a href="">뉴스룸</a></li>
    <li><a href="">채용정보</a></li>
    <li><a href="">투자자 정보</a></li>
    <li><a href="">Airbnb.org 긴급 숙소</a></li>
    <li><a href="">예약 취소 옵션</a></li>
    <li><a href="">이웃 민원 신고</a></li>
  </ul>
  </div>
</section>

<section>
  <div>
  <button>한국어 (KR)</button>
  <button><span>$</span>  <span>KRW</span></button>
  </div>
  
  <div>
    <ul>
      <li><a href=""><img src="" alt="페이스북"></a></li>
      <li><a href=""><img src="" alt="인스타그램"></a></li>
      <li><a href=""><img src="" alt="블로그"></a></li>
    </ul>
  </div>

  <div>© 2026 Airbnb, inc.</div>

  <div>
    <ul>
      <li>개인정보 처리방침</li>
      <li>쿠키 정책</li>
      <li>이용약관</li>
      <li>한국의 변경된 환불 정책</li>
      <li>회사 세부정보</li>
    </ul>
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
</footer>
</template>

<style scoped>

</style>
