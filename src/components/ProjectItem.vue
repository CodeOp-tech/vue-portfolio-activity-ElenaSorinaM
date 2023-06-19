<template>
  <article class="item" @click="handleClick">
    <div class="item__image-container">
      <img class="item__image" :src="project.image" :alt="project.image" />
    </div>
    <div class="item__details">
      <h2 class="item__title">{{ project.title }}</h2>
      <p class="item__description">{{ project.description }}</p>
    </div>
  </article>
</template>

<script>
export default {
  name: "ProjectItem",
  props: ['project'],
  methods: {
    handleClick() {
      this.$emit('select', this.project);
    }
  }
};
</script>


<style scoped>
.item {
  display: flex;
  align-items: center;
  background-color: #f0eef5;
  padding: 10px;
  border-radius: 4px;
  cursor: pointer;
}

.item__image-container {
  width: 100px;
  padding: 10px;
}

.item__image {
  width: 100%;
  height: auto;
}

.item__details {
  flex-grow: 1;
  padding-left: 20px;
}

.item__title {
  color: #6e409b;
  margin-bottom: 10px;
}

.item__description {
  color: #6e409b;
}
</style>