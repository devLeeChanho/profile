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
      <div class="project-content" id="skinable">
        <ul class="project-content-tap">
          <li v-for="(project, index) in projectInfo" 
            v-bind:key="project.title" 
            ref="tab"
            v-bind:class="{active: index === projectInfo.length-1}"
            v-on:click="onClickTap($event, project)">
            {{project.title}}
          </li>    
        </ul>
        <div style="clear:both"></div>
        <article class="project-detail-wrap">
          <div class="project-detail">
            <ul class="detail-os">
              <li v-if="selectedProject.os === 'mobile'">
                <img src="static/assets/image/icon_android.png" alt="실행 환경">
              </li>
              <li v-else>
                <img src="static/assets/image/icon_firefox.png" alt="실행 환경">
                <img src="static/assets/image/icon_chrome.png" alt="실행 환경">
                <img src="static/assets/image/icon_safari.png" alt="실행 환경">
              </li>
            </ul>
            <h3 class="detail-title">
              {{selectedProject.title}}
              <span class="detail-year">({{selectedProject.year}})</span>              
            </h3>
            <ul class="detail-tags">
              <li v-for="tag in selectedProject.tags" v-bind:key="tag">
                {{tag}}
              </li>
            </ul>
            <p class="detail-explain">
              {{selectedProject.explain}}
            </p>
            <div class="detail-role">
              <h4>실제 작업 내용</h4>
              <ul>
                <li v-for="content in selectedProject.role" v-bind:key="content">
                  {{content}}
                </li>
              </ul>
            </div>
          </div>
          <ul class="project-info">
            <li>
              <h4>개발 목적</h4> 
              <span>{{selectedProject.purpose}}</span>
            </li>
            <li>
              <h4>프로젝트 팀원 수</h4> 
              <span>{{selectedProject.manpower}} 명</span>
            </li>
            <li>
              <h4>개발 기간</h4> 
              <span>{{selectedProject.period}} 개월</span>
            </li>
          </ul>
          <!-- 프로젝트 미리보기 -->
          <div class="project-preview">
            <div v-if="selectedProject.preview.video.length" class="preview-video" v-for="(videoUrl, index) in selectedProject.preview.video" v-bind:key="index">
              <video v-bind:src="videoUrl" controls>지원하지 않는 브라우저입니다.</video>              
            </div>
            <div v-if="selectedProject.preview.image.length" class="preview-image-wrap">
              <img src="static/assets/image/image_preview.png" v-on:click="onClickArrow('prev')" class="preview-prev-arrow">                         
              <div class="preview-image">
                <transition name="preview-image">
                  <img v-bind:src="selectedProject.preview.image[selectedPreviewImage]" alt="프로젝트 이미지">                  
                </transition>
              </div>
              <img src="static/assets/image/image_preview.png" v-on:click="onClickArrow('next')" class="preview-next-arrow">           
            </div>
          </div>
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
        selectedProject: projectInfo[projectInfo.length-1],
        selectedPreviewImage: 0
      }
    },
    methods: {
      onClickTap(event, project) {
        this.setSelectedProject(project);
        this.changeTap(event.target);
      },
      onClickArrow(direction) {
        this.selectedPreviewImage++;
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
