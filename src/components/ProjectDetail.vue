<template>
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
      <div class="preview-video" 
      v-if="selectedProject.preview.video.length"
      v-for="(videoUrl, index) in selectedProject.preview.video"
      v-bind:key="index">
      <video v-bind:src="videoUrl" controls>지원하지 않는 브라우저입니다.</video>              
    </div>
    
    <div class="preview-image-wrap" v-if="selectedProject.preview.image.length" >
      <img src="static/assets/image/image_preview.png" 
      v-on:click="onClickArrow('prev')" 
      class="preview-prev-arrow"
      v-bind:class="{'prev-arrow-horizontal': selectedProject.orientation === 'horizontal'}">                         
      <transition-group name="preview" tag="ul" class="preview-image" v-bind:class="{'preview-image-horizontal': selectedProject.orientation === 'horizontal'}">
        <li 
        v-show="index === selectedPreviewIndex"
        v-for="(imgUrl, index) in selectedProject.preview.image" 
        v-bind:key="index">
        <img v-bind:src="imgUrl" alt="프로젝트 이미지">                  
      </li>
    </transition-group>
    <img src="static/assets/image/image_preview.png" 
    v-on:click="onClickArrow('next')" 
    class="preview-next-arrow"
    v-bind:class="{'next-arrow-horizontal': selectedProject.orientation === 'horizontal'}">       
  </div>
</div>
</article>
</template>
<script>
  export default {
    props: ["selectedProject", "selectedPreviewIndex"],
    methods: {
      onClickArrow(direction){
        this.$emit("@onClickArrow", direction);
      }
    }
  }
</script>
