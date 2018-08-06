<template lang="html">
  <div class="users">
    <h1>User Component</h1>
    <ul>
      <li v-for="user in users" :key="user.email">
        {{ user.name }} - {{ user.email }}
        <button v-on:click="deleteUser(user)">X</button>

      </li>
    </ul>

    <form v-on:submit.prevent="addUser">
      <input type="text" v-model="newUser.name" placeHolder="Nombre">
      <input type="email" v-model="newUser.email" placeHolder="Email">
      <button type="submit">Add</button>
    </form>

  </div>
</template>

<script>
export default {
  data() {
    return {
      // users: [
      //   {
      //     name: 'Joe',
      //     email: 'joe@gmail.com',
      //     contacted: false,
      //   },
      //   {
      //     name: 'Jhonny',
      //     email: 'jhonny@gmail.com',
      //     contacted: false,
      //   },
      //   {
      //     name: 'Patan',
      //     email: 'patan@gmail.com',
      //     contacted: false,
      //   },
      // ],
      users: [],
      newUser: {},
    };
  },
  methods: {
    addUser() {
      this.users.push(this.newUser);
      this.newUser = {};
    },
    deleteUser(user) {
      this.users.splice(this.users.indexOf(user), 1);
    },
  },
  created() {
    console.log('Componente creado'); // eslint-disable-line no-console
    this.$http.get('https://jsonplaceholder.typicode.com/users')
      .then(res => this.users = res.body);
  },
};
</script>

<style lang="css">
  .users {
    background: grey;
    color: #fff;
    padding: 20px;
  }
</style>
