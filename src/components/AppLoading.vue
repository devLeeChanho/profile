<template>
  <section class="loading">
    <div class="loading-container">
      <img src="static/assets/image/logo.png" alert="뷰 로고">
      <p class="loading-notice"> 
        조금만 기다려주세요.<br>
        Please wait a minute.
      </p>
      <div class="user-info">
        <span class="browser-check">
          {{browser}}
          <i v-bind:class="{ support : browserSupport }"></i>
        </span>
        <span class="resulution-check">
          {{resolution}}
          <i class="support"></i>
        </span>
      </div>
    </div>
    <div v-bind:class="['loading-circle', {'circle-active': loadingCircle}]"></div>
  </section>
</template>

<script>
export default {
  props: ["loadingCircle"],
  data() {
    return {
      browserSupport: true // 지원하는 브라우저 버전인지 체크
    }
  },
  computed: {
    browser: function() { // 브라우저 정보
      let agent = navigator.userAgent, match;
      let app, version;

      if((match = agent.match(/MSIE ([0-9]+)/)) || (match = agent.match(/Trident.*rv:([0-9]+)/))) app = 'Internet Explorer';
      else if(match = agent.match(/Edge\/([0-9]+)/)) app = 'Edge';
      else if(match = agent.match(/Chrome\/([0-9]+)/)) app = 'Chrome';
      else if(match = agent.match(/Firefox\/([0-9]+)/)) app = 'Firefox';
      else if(match = agent.match(/Safari\/([0-9]+)/)) app = 'Safari';
      else if((match = agent.match(/OPR\/([0-9]+)/)) || (match = agent.match(/Opera\/([0-9]+)/))) app = 'Opera';
      else app = 'Unknown';

      if(app !== 'Unknown') version = match[1];

      //  버전 별 support icon 색상 변경
      //  IE 9버전 이하를 제외한 나머지 브라우저 버전 지원
      if(app === "Internet Explorer"){
        if(version <= 9){
          console.log("IE 9이하 버전");
          this.browserSupport = false;
        }
      }

      return app+" "+version;
    },
    resolution: function() { // 헤상도 정보
      return screen.width+" X "+screen.height;
    }
  }
}
</script>
