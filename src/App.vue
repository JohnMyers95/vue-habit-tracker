<template>
  <div id="app">
    <div class="wrapper">
      <habit v-for="habit in habits" :key="habit.title" :habit="habit" @clicked="saveHabits"></habit>
      <habit></habit>
    </div>
    <new-habit @new-habit="addHabit"/>
  </div>
</template>

<script>
import Habit from "@/components/Habit.vue";
import newHabit from "@/components/newHabit.vue";

export default {
  name: "App",
  components: {
    Habit,
    newHabit,
  },
  data: () => {
    return {
      habits: [],
    };
  },
  methods: {
    addHabit(habit) {
      this.habits.push(habit);
      localStorage.setItem('habits', JSON.stringify(this.habits));
    },
    saveHabits() {
      localStorage.setItem('habits', JSON.stringify(this.habits));
    }
  },
  mounted() {
    if(!localStorage.getItem('backgroundColor')) {
      localStorage.setItem('backgroundColor','peachpuff');
    }
    if(localStorage.getItem('habits')) {
      this.habits = JSON.parse(localStorage.getItem('habits'));
    }
  }
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
