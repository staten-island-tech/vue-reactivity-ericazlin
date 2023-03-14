<template>
  <main>
    <div class="container">
      <div class="texts">
        <div>
          <h1>i love shkola</h1>
          <h1 v-if="number">{{ text }}</h1>

          <ul>
            <li v-for="item in items" :key="item">{{ item }}</li>
          </ul>
        </div>

        <div>
          <button @click="authState" v-if="loggedIn">Log Out yo</button>
          <button @click="authState" v-else>Log In yo</button>
        </div>

        <div>
          <input type="text" placeholder="im going down" v-model="message" />
          <p>{{ message }}</p>
        </div>

        <div>
          <h1>{{ time }}</h1>
        </div>

        <Button @button-click="frigginThing">i am a button</Button>
        <p v-if="loggedIn">{{ poop }}</p>
      </div>

      <div class="cards">
        <Card
          v-for="destination in destinations"
          :key="destination.title"
          :title="destination.title"
          :description="destination.description"
          :image="destination.image"
        />
      </div>
    </div>
  </main>
</template>

<script>
import Button from "./components/Button.vue";
import Card from "./components/Card.vue";

export default {
  data() {
    return {
      text: "ochen da",
      number: true,

      items: ["I", "am", "an", "array", "being", "iterated"],
      loggedIn: false,

      message: "",
      poop: "poop",

      destinations: [
        {
          title: "i am an assortment of words",
          description:
            "not nessecarily with any importance or meaning behind them",
          image:
            "https://images.unsplash.com/photo-1514496959998-c01c40915c5f?ixlib=rb-4.0.3&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=1170&q=80",
        },
        {
          title: "i dont know what else to write :(",
          description:
            "i only need one more after this so i can use dynamic props",
          image:
            "https://images.unsplash.com/photo-1678398176993-dc9cb4df6763?ixlib=rb-4.0.3&ixid=MnwxMjA3fDB8MHx0b3BpYy1mZWVkfDIyfGJvOGpRS1RhRTBZfHxlbnwwfHx8fA%3D%3D&auto=format&fit=crop&w=500&q=60 ",
        },
        {
          title: "unsplash is pretty cool for free photos",
          description:
            "i like snow and mountains and nature and stuff like that",
          image:
            "https://images.unsplash.com/photo-1678497180488-d0f1cf12e61c?ixlib=rb-4.0.3&ixid=MnwxMjA3fDB8MHx0b3BpYy1mZWVkfDIwfGJvOGpRS1RhRTBZfHxlbnwwfHx8fA%3D%3D&auto=format&fit=crop&w=500&q=60",
        },
      ],
    };
  },

  components: {
    Button,
    Card,
  },

  computed: {
    time: function () {
      const time = new Date();
      return `${time.getHours()}:${time.getMinutes()}:${time.getSeconds()}`;
    },
  },
  methods: {
    authState: function () {
      if (this.loggedIn === false) {
        this.loggedIn = true;
      } else {
        this.loggedIn = false;
      }
    },
    frigginThing: function () {
      if (this.poop === "") {
        this.poop = "poop";
      } else {
        this.poop = "";
      }
    },
  },
};
</script>

<style>
.container {
  display: flex;
  justify-content: space-around;
  margin: auto;
}

.cards {
  display: flex;
  flex-direction: column;
}

.texts {
  display: flex;
  flex-direction: column;
  align-items: center;
  width: 40vw;
}

.texts input,
button {
  width: 30vw;
}
</style>
