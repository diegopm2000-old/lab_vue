<template>
  <div class="test">
    <!-- <div v-html="myHtml"></div> -->
    <!-- <div v-text="titulo"></div> -->
    <div v-text="msg"></div>
    <div v-if="showName">
      <p>{{ user.firstName + ' ' + user.lastName}}</p>
    </div>
    <div v-if="showName">
      <p>{{ fullName }}</p>
    </div>
    <div v-else>
      <p>No puedo mostrar el nombre</p>
    </div>
    <hr>
    <ul>
      <li v-for="task in tasks" :key="task.title">
        {{ task.title }}
      </li>
    </ul>
    <input type="text" v-model="user.firstName"/>
    <button type="button" v-on:click="saludar(user.firstName)">
      CLICK ME
    </button>
    <hr>
    <input type="text" v-on:keyup="typing"/>
    <hr>
    <input type="text" v-on:keyup.enter="enter"/>
  </div>
</template>

<script>
export default {
  data() {
    return {
      titulo: 'Hola Vuejs',
      user: {
        firstName: 'John',
        lastName: 'Doe',
      },
      myHtml: '<h3>Hola vue</h3>',
      showName: true,
      tasks: [
        { title: 'eat' },
        { title: 'dinner' },
        { title: 'play' },
      ],
    };
  },
  methods: {
    saludar(name) {
      alert.log(`Hola ${name}`); // eslint-disable-line no-alert
    },
    typing(e) {
      console.log(e.target.value); // eslint-disable-line no-console
    },
    enter() {
      console.log('Pulsado enter!'); // eslint-disable-line no-console
    },
  },
  computed: {
    fullName() {
      return `${this.user.firstName} ${this.user.lastName} generado en computed`;
    },
  },
  props: {
    msg: {
      type: String,
      default: 'Mensaje por defecto',
    },
  },
};
</script>

<style media="screen">
  .test {
    background-color: #eee;
  }
</style>
