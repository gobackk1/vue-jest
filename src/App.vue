<template>
  <div id="app">
    <div v-if="selectedUser">
      selectedUser:
      {{selectedUser}}
    </div>
    <UsersList :users="users" @select="onSelect" @remove="onRemove" />
  </div>
</template>

<script>
import UsersList from "./components/UsersList.vue";
import users from "./users.json";
export default {
  name: "app",
  data() {
    return {
      users: null,
      selectedUserId: null
    };
  },
  created() {
    this.users = users
  },
  computed: {
    selectedUser() {
      return this.users.find(user => user.id === this.selectedUserId);
    }
  },
  methods:{
    onSelect({id}){
      this.selectedUserId = id
    },
    onRemove({id}){
      const index = this.users.findIndex((user)=> user.id === id)
      this.users.splice(index,1)
    },
  },
  components: {
    UsersList,
  },
};
</script>

<style lang="scss">
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

h1,
h2 {
  font-weight: normal;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: inline-block;
  margin: 0 10px;
}

a {
  color: #42b983;
}
</style>
