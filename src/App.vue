<template>
  <div class="main-div">
    <h1>Hello World</h1>
    <div class="buttons-div">
     <button class="nav-button" @click="isAdmin = true">ADMIN</button>
    <button class="nav-button" @click="isAdmin = false">USER</button>
    </div> 
    <admin-view v-if="isAdmin" @createProject="addProject" />
    <user-view v-else /> 
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
      allProjects: []
    };
  },
  methods: {
    addProject(project) {
      this.allProjects.push(project);
    }
  }
};
</script>

<style>
.main-div {
  display: flex;
  flex-direction: column;
  align-items: center;
  width: 100%;
  height: auto;
  font-family:Arial, Helvetica, sans-serif;
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
}
.form-div{
  display: flex;
  flex-direction: row;
  align-items: center;
  gap: 10px;

}
button{
  font-family: Verdana, Geneva, Tahoma, sans-serif;
  border-radius: 15px;
  border: none;
  text-align: center;
  padding: 15px 30x;
  cursor: pointer;
  background-color:ghostwhite;
  color: green;
}
.input-form{
  width: 150px;
  background-color:aliceblue;w  
}

</style>
