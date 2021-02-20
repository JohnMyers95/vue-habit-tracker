<template>
  <div id="app">
    <div class="wrapper">
      <habit v-for="habit in habits" :key="habit.title" :habit="habit"></habit>
    </div>
  </div>
</template>

<script>
import Habit from "@/components/Habit.vue";

export default {
  name: "App",
  components: {
    Habit,
  },
  data: () => {
    return {
      habits: [
        {
          title: "Drink water",
          goal: 5,
        },
        {
          title: "Go Outside",
          goal: 2,
        }
      ],
    };
  },
};
</script>

<style>
html {
  background-color: peachpuff;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
.wrapper {
  display: grid;
  grid-template-columns: 1fr 1fr;
  grid-gap: 20px;
  margin: 10%;
}
</style>
