<template>
  <section class="project">
    <div class="project-container" v-observe-visibility="visibleAnimation">
      <h2 v-observe-visibility="visibleAnimation">
        <span>
          Student <br>
          Project  
        </span>
      </h2>
      <div style="clear: both;"></div>
      <div class="project-content" id="skinable" v-observe-visibility="visibleAnimation">
        <project-tap 
          v-bind:project-info="projectInfo"
          v-on:@onClickTap="onClickTap">
        </project-tap>
        <div style="clear:both"></div>
        <project-detail
          v-on:@onClickArrow="onClickArrow"
          v-bind:selected-project="selectedProject" 
          v-bind:selected-preview-index="selectedPreviewIndex">
        </project-detail>
      </div>
    </div>
  </section>
</template>
<script>
import projectInfo from "../other/project_info.json";
import ProjectTap from "./ProjectTap.vue";
import ProjectDetail from "./ProjectDetail.vue";

  export default {
    components: {
      "project-detail": ProjectDetail,
      "project-tap": ProjectTap
    },
    data() {
      return {
        projectInfo: projectInfo,
        selectedProject: projectInfo[projectInfo.length-1],
        selectedPreviewIndex: 0
      }
    },
    methods: {
      onClickTap(event, project) {
        this.selectedPreviewIndex = 0; // 미리보기 이미지 인덱스 초기화
        this.setSelectedProject(project);
        this.changeTap(event.target);
      },
      onClickArrow(direction) {
        if(direction === "prev")
          this.prevPreview();
        else
          this.nextPreview();
      },
      prevPreview() {
        if(this.selectedPreviewIndex === 0){
          this.selectedPreviewIndex = this.selectedProject.preview.image.length-1;
        }else{
          this.selectedPreviewIndex--;
        }
      },
      nextPreview() {
        if(this.selectedPreviewIndex === this.selectedProject.preview.image.length-1){
          this.selectedPreviewIndex = 0;
        }else{
          this.selectedPreviewIndex++;
        }
      },
      setSelectedProject(project) {
        this.selectedProject = project;        
      },
      changeTap(tab){
        if(tab.classList.contains("active"))
          return;

        let tabs = tab.parentNode.childNodes;

        for (let i = 0; i < tabs.length; i++){
          tabs[i].classList.remove('active');
        }
        tab.classList.add("active");
      },
      // Intersection Observer API
      visibleAnimation(isVisible, entry) {
        if(isVisible)
          entry.target.setAttribute("style", "opacity:1; transform: translateY(0);");
        else
          entry.target.setAttribute("style", "opacity:0; transform: translateY(30%);");
      }
    }
  }
</script>
