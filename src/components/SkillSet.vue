<template>
  <section class=skillset>
    <div class="skillset-container">
      <h2 v-observe-visibility="visibleAnimation">
        <span class="skillset-title">SKILL SET</span>
        <p class="skillset-notice">박스위에 커서를 올리거나 터치하세요</p>
      </h2>
      <div style="clear:both"></div>
      <skill-list v-bind:skills="skills"></skill-list>
    </div>
  </section>
</template>
<script>

import skillSet from "../other/skill_set.json";
import SkillList from "./SkillList.vue";

export default {
  data() {
    return {
      skills: skillSet
    }
  },
  components: {
    "skill-list": SkillList
  },
  methods: {
    // Intersection Observer API
    visibleAnimation(isVisible, entry) {
      if(isVisible)
        entry.target.setAttribute("style", "opacity:1; transform: translateY(0);");
      else
        entry.target.setAttribute("style", "opacity:0; transform: translateY(100%);");
    }
  }
}
</script>
