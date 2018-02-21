<template>
  <ul class="project-content-tap">
    <li v-for="(project, index) in projectInfo" 
      v-bind:key="project.title"
      v-bind:class="{active: index === projectInfo.length-1}"
      v-on:click="onClickTap($event, project)">
      {{project.title}}
  </li>    
</ul>
</template>
<script>
  export default {
    props: ["projectInfo"],
    methods: {
      onClickTap(event, project) {
        this.$emit("@onClickTap", event, project);
      }
    }
  }
</script>
