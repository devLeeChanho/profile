<template>
  <ul class="skill-list">
    <li v-for="(item, index) in skills" v-bind:key="index" v-bind:class="(index === 0 || index === 6 || index === 9) ? 'list-item-4' : 'list-item-1'" v-observe-visibility="visibleAnimation">
      <h4 class="item-title">{{item.title}}</h4>
      <div class="item-count-project">프로젝트수: {{item.countProjects}}개+</div>
      <div class="item-star">{{item.star}}</div>
      <img v-bind:src="item.imgUrl" alt="language logo">
      <div class="skill-detail">
        <p v-for="(description, index) in item.skillDescription" v-bind:key="index">
          {{description}}          
        </p>
      </div>
    </li>
    <div style="clear:both"></div>        
  </ul>
</template>
<script>
  export default {
    props: ["skills"],
    methods: {
      // Intersection Observer API
      visibleAnimation(isVisible, entry) {
        if(isVisible)
          entry.target.setAttribute("style", "opacity:1; transform: translateY(0);");
        else
          entry.target.setAttribute("style", "opacity:0; transform: translateY(50%);");
      }
    }
  }
</script>
