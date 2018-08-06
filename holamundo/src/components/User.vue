<template lang="html">
  <div class="users">
    <h1>User Component</h1>
    <ul>
      <li v-for="user in users">
        {{ user.name }} - {{ user.email }}
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
      users: [
        {
          name: 'Joe',
          email: 'joe@gmail.com',
          contacted: false,
        },
        {
          name: 'Jhonny',
          email: 'jhonny@gmail.com',
          contacted: false,
        },
        {
          name: 'Patan',
          email: 'patan@gmail.com',
          contacted: false,
        },
      ],
      newUser: {},
    };
  },
  methods: {
    addUser() {
      this.users.push(this.newUser);
      this.newUser = {};
    },
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
