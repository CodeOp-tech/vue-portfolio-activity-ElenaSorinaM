<template>
  <div class="main-div">
    <h1 class="title">Portfolio</h1>
    <div class="buttons-div">
      <button class="nav-button" @click="isAdmin = true">ADMIN</button>
      <button class="nav-button" @click="isAdmin = false">USER</button>
    </div>
    <admin-view v-if="isAdmin" @createProject="addProject" />
    <user-view v-else :projects="allProjects" @selectProject="selectProject" />
    <div v-if="selectedProject" class="selected-project">
      <h2 class="selected-project__title">{{ selectedProject.title }}</h2>
      <img :src="selectedProject.image" :alt="selectedProject.image" class="selected-project__image" />
      <p class="selected-project__description">{{ selectedProject.description }}</p>
    </div>
  </div>
</template>



<script>
import AdminView from "./components/AdminView.vue";
import UserView from "./components/UserView.vue";

export default {
  name: "app",
  components: {
    userView: UserView,
    adminView: AdminView
  },
  data() {
    return {
      isAdmin: true,
      allProjects: [],
      selectedProject: null
    };
  },
  methods: {
    addProject(project) {
      this.allProjects.push(project);
    },
    selectProject(project) {
      this.selectedProject = project;
    }
  }
};
</script>

<style scoped>
.main-div {
  max-width: 800px;
  margin: 0 auto;
  padding: 20px;
  background-color: #f5f3f8;
}

.title {
  color: #6e409b;
}

.buttons-div {
  margin-bottom: 20px;
  display: flex;
  justify-content: center;
}

.nav-button {
  color: #fff;
  background-color: #6e409b;
  border: none;
  padding: 10px 20px;
  margin-right: 10px;
  cursor: pointer;
}

.selected-project {
  margin-top: 20px;
  padding: 20px;
  background-color: #e5dff2;
  border-radius: 4px;
}

.selected-project__title {
  color: #6e409b;
}

.selected-project__image {
  max-width: 100%;
  height: auto;
  margin-bottom: 10px;
}

.selected-project__description {
  color: #6e409b;
}
/* html, body{
  height: 100%;
}
#app {
height: 100%;
} */
/* .main-div {
  display: flex;
  flex-direction: column;
  align-items: center;
  width: 100%;
  height: 100%;
  font-family:Arial, Helvetica, sans-serif;
  justify-content: center;
}

h1{
  font-style: normal; 
  font-weight:700;
  font-size: 50px;
  color:green;
}
.buttons-div{
  display: flex;
  flex-direction: row;
  gap: 10px;
  padding-bottom: 20px;
}
.nav-button{
  background-color:darkseagreen;
  text-align: center;
  padding: 15px 32px;
  color: white;
} */
</style>



