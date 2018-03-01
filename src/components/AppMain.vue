<template>
  <section ref="main" class="main">
    <div class="main-container">
      <div class="main-left">
        <h2 v-observe-visibility="visibleAnimation">
          LEE CHANHO <br>
          I`M A <br>
          Front-End Developer
        </h2>
      </div>
      <div class="main-right">
        <img v-observe-visibility="visibleAnimation" class="lamp" src="static/assets/image/image_lamp.png" alt="전등">
        <img v-observe-visibility="visibleAnimation" class="starbucks" src="static/assets/image/image_starbucks.png" alt="스타벅스 커피">
        <img v-observe-visibility="visibleAnimation" class="macbook" src="static/assets/image/image_macbook.png" alt="맥북 이미지">
      </div>
    </div>
    <div class="indicator-container">
      <div class="indicator-arrow top">
        <div class="base"></div>
        <div class="arrowpoint"></div>
      </div>
      <div class="indicator-arrow bottom">
        <div class="base"></div>
        <div class="arrowpoint"></div>
      </div>
    </div>
  </section>
</template>
<script>
export default {
  mounted() {
    this.mainInit();
  },
  methods: {
    mainInit() {
      this.mainScroll();
    },
    mainScroll() {
 
      let $htmlAndBody = $("html, body"),
          $main = $("section.main");

      let mainTop = 0, // 메인 상단 좌표 값
          mainBottom = 0, // 메인 하단 좌표 값
          lastScollTop = -1; // 마지막 스크롤 위치
      
      $(window).on("scroll", function() {
        mainTop = $main.offset().top;
        mainBottom = mainTop+$main.height()-61;

        if($(this).scrollTop() > mainTop && $(this).scrollTop() < mainBottom){
          if($htmlAndBody.is(':animated')) return

          if($(this).scrollTop() > lastScollTop){
            // scroll down
            $htmlAndBody.animate({scrollTop : mainBottom}, 400);
            lastScollTop = mainBottom;
          }else{
            // scroll up
            $htmlAndBody.animate({scrollTop : mainTop}, 400);
            lastScollTop = mainTop;            
          }
        }
      });
    },
    visibleAnimation(isVisible, entry) {
      if(isVisible){
        entry.target.setAttribute("style", "opacity:1; transform: translateY(0);");
      }
      else{
        entry.target.setAttribute("style", "opacity:0; transform: translateY(-50%);");
      }
    }
  }
}
</script>
