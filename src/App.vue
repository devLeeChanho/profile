<template>
  <div id="app">
    <app-loading></app-loading>
    <global-nav></global-nav>
    <app-main></app-main>
    <profile-section></profile-section>
    <skill-set></skill-set>
    <project-student></project-student>
    <project-employee></project-employee>
  </div>
</template>

<script>
import AppLoading from "./components/AppLoading.vue";
import GlobalNav from "./components/GlobalNav.vue";
import AppMain from "./components/AppMain.vue";
import ProfileSection from "./components/ProfileSection.vue";
import SkillSet from "./components/SkillSet.vue";
import ProjectStudent from "./components/ProjectStudent.vue";
import ProjectEmployee from "./components/ProjectEmployee.vue";

export default {
  name: 'App',
  components: {
    "app-loading": AppLoading,
    "global-nav": GlobalNav,
    "app-main": AppMain,
    "profile-section": ProfileSection,
    "skill-set": SkillSet,
    "project-student": ProjectStudent,
    "project-employee": ProjectEmployee
  },
  created() {
    // 브라우저 크기 최대화 메소드
    this.browserMaximize();
  },
  methods: {
    browserMaximize(){
      
    }
  }
}
</script>