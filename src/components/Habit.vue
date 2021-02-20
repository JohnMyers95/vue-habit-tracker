<template>
  <div v-if="this.habit" :class="cssClass" @click="addProgress">
    <div class="title">
      {{ habit.title }}
    </div>
    <div class="progress">{{ habit.progress }} / {{ habit.goal }}</div>
  </div>
  <div v-else class="habit new" @click="newHabit">
      <div>+</div>
  </div>
</template>
<script>
export default {
  data: () => {
    return {
      cssClass: "habit",
    };
  },
  props: {
    habit: {
      type: Object,
      required: false,
    },
  },
  methods: {
    addProgress() {
      if (this.habit.progress < this.habit.goal) {
        this.habit.progress++;
      }
      if (this.habit.progress == this.habit.goal) {
        this.cssClass = "habit completed";
      }
      this.$emit('clicked');
    },
    newHabit() {
      this.$emit('clicked');
    }
  },
  created: () => {},
};
</script>

<style scoped>
.habit {
  display: grid;
  grid-template-columns: 1fr;
  grid-template-rows: 1fr 2fr;
  border-radius: 30px;
  background-color: palegoldenrod;
  border: 0.5px solid black;
  box-shadow: 4px 4px 2px 1px #8a8a8a;
  padding: 10px;
  align-items: center;
  transition: 0.5s;
}
.title {
  display: flex;
  justify-content: center;
  margin: 5px auto;
  font-size: 1.2em;
  font-weight: bold;
}
.progress {
  font-size: 2em;
  font-weight: bold;
}
.completed {
  background-color: greenyellow;
}
.new {
    grid-template-columns: 1fr;
    grid-template-rows: 1fr;
    font-size: 2em;
    font-weight: bold;
}
</style>
