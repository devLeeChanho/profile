<template>
  <section ref="main" class="main">
    <div class="main-container">
      <div class="main-left">
        <h2>
          LEE CHANHO <br>
          I`M A <br>
          Front-End Developer
        </h2>
      </div>
      <div class="main-right">
        <img class="lamp" src="static/assets/image/image_lamp.png" alt="전등">
        <img class="starbucks" src="static/assets/image/image_starbucks.png" alt="스타벅스 커피">
        <img class="macbook" src="static/assets/image/image_macbook.png" alt="맥북 이미지">
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

      // jquery 미사용
      // let lastScollTop = 0;
      // let scrollEventState = false;
      // window.addEventListener("scroll", function(e) {
      //   if(this.pageYOffset > mainTop && this.pageYOffset < mainBottom){
      //     if(scrollEventState) return;
      //     else scrollEventState = true; 

      //     if(this.pageYOffset > lastScollTop){
      //       // scroll down
      //       this.scroll({
      //         top: mainBottom,
      //         behavior: "smooth"
      //       });
      //     }else{
      //       // scroll up
      //       this.scroll({
      //         top: mainTop,
      //         behavior: "smooth"
      //       });
      //     }

      //     lastScollTop = this.pageYOffset;
      //     setTimeout(function(){
      //       scrollEventState = false;
      //     }, 500);
      //   }
      // });
    }
  }
}
</script>
