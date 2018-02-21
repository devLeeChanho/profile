<template>
  <section class=skillset>
    <div class="skillset-container">
      <h2>
        <span>Skill Set</span>
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
  }
}
</script>
