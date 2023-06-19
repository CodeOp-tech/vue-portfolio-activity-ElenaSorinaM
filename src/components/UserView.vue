<template>
  <div v-if="projects.length > 0" class="grid-container">
    <project-item
      v-for="project in projects"
      :key="project.title"
      :project="project"
      @select="handleSelect"
    />
  </div>
  <div v-else>
    <h4 class="add-project-text">Add a project</h4>
  </div>
</template>


<script>
import ProjectItem from './ProjectItem.vue';
export default {
  components: { ProjectItem },
  name: "UserView",
  props: ["projects"],
  methods: {
    handleSelect(project) {
      this.$emit("selectProject", project);
    }
  }
};
</script>

<style scoped>
.grid-container {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
  grid-gap: 20px;
}

.add-project-text {
  color: #6e409b;
}
</style>