<template>
  <nav ref="gnb" class="gnb">
    <div class="gnb-container">
      <div class="left-gnb" v-on:click="onClickMenu">
        <i class="menu-icon fas fa-bars"></i>
        <ul class="section-title">
          <!-- MAIN, PROFILE, SKILLSET, PROJECTS -->
          <li>{{selectedSection}}</li>
        </ul>
      </div>
      <transition name="gnb-hide">
        <ul class="left-gnb-hide" v-show="hideMenuState">
          <span></span>
          <li 
            v-for="(list, index) in sectionList" 
            v-bind:key="index"
            v-on:click="onClickMenuList(list)">
              {{list}}
          </li>
        </ul>
      </transition>
      <ul class="right-gnb">
        <a href="mailto:devho813@gmail.com"><li><img src="static/assets/image/icon_email.png" alt="이메일 아이콘"></li></a>
        <a href="http://devleechanho.tistory.com" target="_blank"><li><img src="static/assets/image/icon_blog.png" alt="블로그 아이콘"></li></a>
        <a href="https://github.com/devLeeChanho" target="_blank"><li><img src="static/assets/image/icon_github.png" alt="깃허브 아이콘"></li></a>
      </ul>
    </div>
  </nav>
</template>
<script>
export default {
  data() {
    return {
      sectionList: ["MAIN", "PROFILE", "SKILLSET", "PROJECTS"],      
      selectedSection: "MAIN",
      hideMenuState: false
    }
  },
  mounted() {
    this.gnbInit();
  },
  methods: {
    gnbInit() {
      let gnb = this.$refs.gnb;

      window.addEventListener('scroll', function() {
        if(this.pageYOffset > 0){
          gnb.classList.add("gnb-scroll");
        }else{
          gnb.classList.remove("gnb-scroll");          
        }
      });
    },
    onClickMenu() {
      this.hideMenuState = !this.hideMenuState;
    },
    onClickMenuList(list) {
      this.$emit("@onClickMenuList", list);
    }
  }
}
</script>
