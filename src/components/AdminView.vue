<template>
  <div class="form-div">
    <div class="form-h3">
      <h3>Add new project</h3>
    </div>
    <form class="input-form" @submit.prevent="handleSubmit">
      <div class="form-group">
        <label for="project-title">Title</label>
        <input v-model="title" type="text" id="project-title" name="title" />
      </div>
      <div class="form-group">
        <label for="project-image">Image</label>
        <input v-model="image" type="url" id="project-image" name="image" />
      </div>
      <div class="form-group">
        <label for="project-description">Description</label>
        <textarea v-model="description" id="project-description" name="description"></textarea>
      </div>
      <div class="form__submit-button">
        <button class="submit-button">Submit</button>
      </div>
    </form>
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
      })
      this.reset()
    },
    reset(){
      this.image = "";
      this.title = "";
      this.description = "";
    }
  }
};
</script>

<style scoped>
.form-div {
  display: flex;
  flex-direction: column;
  align-items: center;
}

.form-h3 {
  margin-bottom: 20px;
  text-align: center;
}

.input-form {
  display: flex;
  flex-direction: column;
  align-items: center;
  width: 300px;
}

.form-group {
  margin-bottom: 20px;
  width: 100%;
}

.form-group label {
  display: block;
  margin-bottom: 5px;
}

.form-group input,
.form-group textarea {
  width: 100%;
  padding: 8px;
  border: 1px solid #ccc;
  border-radius: 4px;
}

.submit-button {
  padding: 10px 20px;
  background-color: #6e409b;
  color: #ffffff;
  border: none;
  border-radius: 4px;
  cursor: pointer;
  font-size: 16px;
  transition: background-color 0.3s ease;
}

.submit-button:hover {
  background-color: #58387a;
}
</style>
