<template>
  <div id="app" class="app">
    <app-loading v-if="loadingState"></app-loading>
    <global-nav v-on:@onClickMenuList="onClickMenuList"></global-nav>
    <app-main ref="appMain"></app-main>
    <profile-section ref="profileSection"></profile-section>
    <skill-set ref="skillSet"></skill-set>
    <project-student ref="projectStudent"></project-student>
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
  data() {
    return {
      loadingState: true
    }
  },
  methods: {
    onChangeLoadingState() {
      setTimeout(() => {
        this.loadingState = false;
      }, 3000);
    },
    onClickMenuList(list) {
      // MAIN, PROFILE, SKILLSET, PROJECTS      
      switch (list) {
        case "MAIN":
          this.$refs.appMain.$el.scrollIntoView({behavior: 'smooth'});
          break;
        case "PROFILE":
          this.$refs.profileSection.$el.scrollIntoView({behavior: 'smooth'});
          break;
        case "SKILLSET":
          this.$refs.skillSet.$el.scrollIntoView({behavior: 'smooth'});
          break;
        case "PROJECTS":
          this.$refs.projectStudent.$el.scrollIntoView({behavior: 'smooth'});
          break;
      }
    }
  },
  created() {   
    this.onChangeLoadingState();
  }
}
</script>