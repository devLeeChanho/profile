<template>
  <section class="profile" v-observe-visibility="backgroundAnimation">
    <div class="profile-container">
      <h2 v-observe-visibility="visibleAnimation">
        <span>PROFILE</span>
      </h2>
      <div class="profile-content" v-observe-visibility="visibleAnimation">
        <ul>
          <li>
            <h3>NAME</h3>
            <p>Chanho Lee (이찬호) 李澯昊</p>
          </li>
          <li>
            <h3>BIRTH</h3>
            <p>13th August 1993 (26세)</p>
          </li>
          <li>
            <h3>ADDRESS</h3>
            <p>Meokgol, Korea (서울시 중랑구 묵1동)</p>
          </li>
          <li>
            <h3>HOBBY</h3>
            <p>#개발 &nbsp;#<img class="soccer-ball" src="static/assets/image/image_soccerball.jpeg" alt="축구공">&nbsp;#EPL 시청 &nbsp;#배틀그라운드</p>
          </li>
          <li>
            <h3>CERTIFICATE & AWARD</h3>
            <p>
              * 정보처리기사 <br>
              * 충청북도 모바일 앱 공모전 최우수상 수상 <br>
              * 졸업작품 전시회 우수상
            </p>
          </li>
        </ul>
      </div>
      <!-- <div class="profile-aside">
        <img class="identification-picture" src="static/assets/image/identification_picture.jpg" alt="이력서 사진"> -->
        <!-- 테스트 이미지 나중에 학위증 대체 -->
        <!-- <img class="contest-image" src="static/assets/image/photo_mobile_contest.jpg" alt="공모전 사진">
      </div> -->
      <div style="clear: both;"></div>
    </div>
  </section>
</template>
<script>
export default {
  methods:{
    // Intersection Observer API
    backgroundAnimation(isVisible, entry) {
      if(isVisible){
        entry.target.setAttribute("style", "background-position: 100% 80%;");
      }else{
        entry.target.setAttribute("style", "background-position: 100% 130%");
      }
    },
    visibleAnimation(isVisible, entry) {
      if(isVisible)
        entry.target.setAttribute("style", "opacity:1; transform: translateY(0);");
      else
        entry.target.setAttribute("style", "opacity:0; transform: translateY(50%);");
    }
  }
}
</script>
