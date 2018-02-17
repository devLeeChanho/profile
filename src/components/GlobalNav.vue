<template>
  <nav class="gnb">
    <div class="gnb-container">
      <div class="left-gnb">
        <i class="menu-icon fas fa-bars"></i>
        <ul class="section-title">
          <!-- MAIN, PROFILE, SKILLSET, PROJECTS -->
          <li>{{selectedSection}}</li>
        </ul>
      </div>
      <ul class="right-gnb">
        <a href="mailto:devho813@gmail.com"><li><img src="../assets/email_icon.png" alt="이메일 아이콘"></li></a>
        <a href="http://devleechanho.tistory.com" target="_blank"><li><img src="../assets/blog_icon.png" alt="블로그 아이콘"></li></a>
        <a href="https://github.com/devLeeChanho" target="_blank"><li><img src="../assets/github_icon.png" alt="깃허브 아이콘"></li></a>
      </ul>
    </div>
  </nav>
</template>
<script>
export default {
  data() {
    return {
      selectedSection: "MAIN"
    }
  }
}
</script>
