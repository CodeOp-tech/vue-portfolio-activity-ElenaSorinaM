<template>
  <div class="form-div">
    Title
    <input class="input-form" v-model="title" />
    <button class="submit-button" @click="handleSubmit">SUBMIT</button>
  </div>
</template>

<script>
export default {
  name: "AdminView",
  data() {
    return {
      title: "",
      image: "",
      description: ""
    };
  },
  methods: {
    handleSubmit() {
      this.$emit("createProject", {
        title: this.title,
        image: this.image,
        description: this.description
      });
    }
  }
};
</script>

<style>

</style>
