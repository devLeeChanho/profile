<template>
  <section class="project">
    <div class="project-container">
      <h2>
        <span>
          Student <br>
          Project  
        </span>
      </h2>
      <div style="clear: both;"></div>
      <div class="project-content tabbed skin-turquoise round" id="skinable">
        <ul>
          <li v-for="(project, index) in projectInfo" 
            v-bind:key="project.title" 
            ref="tab"
            v-bind:class="{active: index === projectInfo.length-1}"
            v-on:click="onClickTap($event, project)">
            {{project.title}}
          </li>    
        </ul>
        <div style="clear:both"></div>
        <article class="project-detail">
          {{selectedProject.os}}<br>
          {{selectedProject.title}}<br>
          {{selectedProject.year}}<br>
          {{selectedProject.tags[0]}}<br>
          {{selectedProject.purpose}}<br>
          {{selectedProject.manpower}}<br>
          {{selectedProject.period}}<br>
          {{selectedProject.explain}}<br>
          {{selectedProject.role[0]}}<br>
        </article>
      </div>
    </div>
  </section>
</template>
<script>
import projectInfo from "../other/project_info.json";

  export default {
    data() {
      return {
        projectInfo: projectInfo,
        selectedProject: projectInfo[projectInfo.length-1]
      }
    },
    methods: {
      onClickTap(event, project) {
        this.setSelectedProject(project);
        this.changeTap(event.target);
      },
      setSelectedProject(project) {
        this.selectedProject = project;        
      },
      changeTap(tab){
        if(tab.classList.contains("active"))
          return;

        let tabs = this.$refs.tab;

        for (let i = 0; i < tabs.length; i++){
          tabs[i].classList.remove('active');
        }
        
        tab.classList.add("active");
      }
    }
  }
</script>
