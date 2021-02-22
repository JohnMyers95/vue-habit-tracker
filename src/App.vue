<template>
  <div id="app">
    <div class="wrapper">
      <habit
        v-for="habit in habits"
        :key="habit.title"
        :habit="habit"
        @clicked="saveHabits"
      ></habit>
      <habit @clicked="addNewHabitVisible = true"></habit>
    </div>
    <transition name="fade">
      <new-habit
        v-show="addNewHabitVisible"
        @new-habit="addHabit"
        @close="addNewHabitVisible = false"
      ></new-habit>
    </transition>
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
      addNewHabitVisible: false,
    };
  },
  methods: {
    addHabit(habit) {
      this.habits.push(habit);
      localStorage.setItem("habits", JSON.stringify(this.habits));
      this.addNewHabitVisible = false;
    },
    saveHabits() {
      localStorage.setItem("habits", JSON.stringify(this.habits));
      localStorage.setItem("lastSaveTime", Date.now());
    },
  },
  mounted() {
    if (!localStorage.getItem("backgroundColor")) {
      localStorage.setItem("backgroundColor", "peachpuff");
    }
    if (localStorage.getItem("habits")) {
      this.habits = JSON.parse(localStorage.getItem("habits"));
    }
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
.fade-enter-active, .fade-leave-active {
  transition: opacity .1s
}
.fade-enter, .fade-leave-to {
  opacity: 0
}
</style>
