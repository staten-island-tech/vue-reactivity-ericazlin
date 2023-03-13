<template>
  <main>
    <h1>i love shkola</h1>
    <h1 v-if="number">{{ text }}</h1>

    <ul>
      <li v-for="item in items" :key="item">{{ item }}</li>
    </ul>


    <button @click="authState" v-if="loggedIn">Log Out yo</button>
    <button @click="authState" v-else>Log In yo</button>

    <br>
    <input type="text" placeholder="im going down" v-model="message">
    <p>{{ message }}</p>

    <h1>{{ time }}</h1>

    <Button @button-click="frigginThing">i am a button</Button>
    <p v-if="loggedIn">{{ poop }}</p>
  </main>
</template>

<style scoped></style>

<script>

import Button from './components/Button.vue'

export default {
  data() {
    return {
      text: "ochen da",
      number: true,

      items: ["I", "am", "an", "array", "being", "iterated"],
      loggedIn: false,

      message: "",
      poop: "",
    };
  },

  components: {
    Button,
  },

  computed: {
    time: function () {
      const time = new Date;
      return `${time.getHours()}:${time.getMinutes()}:${time.getSeconds()}`
    }
  },
  methods: {
    authState: function () {
      if (this.loggedIn === false) {
        this.loggedIn = true;
      }
      else {
        this.loggedIn = false;
      }
    },
    frigginThing: function () {
      if (this.poop === "") {
        this.poop = "poop"
      }
      else {
        this.poop = ""
      }
    },
  }
};
</script>
