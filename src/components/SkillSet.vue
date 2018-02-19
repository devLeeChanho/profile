<template>
  <section class=skillset>
    <div class="skillset-container">
      <h2>
        <span>Skill Set</span>
      </h2>
      <div style="clear:both"></div>
      <ul class="skill-list">
        <li v-for="(item, index) in skills" v-bind:key="index" v-bind:class="(index === 0 || index === 6 || index === 9) ? 'list-item-4' : 'list-item-1'">
          <h4 class="item-title">{{item.title}}</h4>
          <div class="item-count-project">프로젝트수: {{item.countProjects}}개+</div>
          <div class="item-star">{{item.star}}</div>
          <img v-bind:src="item.imgUrl" alt="language logo">
        </li>
        <div style="clear:both"></div>        
      </ul>
    </div>
  </section>
</template>
<script>

import skillSet from "../other/skill_set.json";

export default {
  data() {
    return {
      skills: skillSet
    }
  }
}
</script>
