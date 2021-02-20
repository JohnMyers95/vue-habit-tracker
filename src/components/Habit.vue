<template>
  <div :class="cssClass" @click="addProgress">
    <div class="title">
      {{ habit.title }}
    </div>
    <div class="progress">{{ this.progress }} / {{ habit.goal }}</div>
  </div>
</template>
<script>
export default {
  data: () => {
    return {
      progress: 0,
      cssClass: "habit",
    };
  },
  props: {
    habit: {
      type: Object,
      required: true,
    },
  },
  methods: {
    addProgress() {
      if (this.progress < this.habit.goal) {
        this.progress++;
      }
      if (this.progress == this.habit.goal) {
        this.cssClass = "habit completed";
      }
    },
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
  aspect-ratio: 1/1;
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
</style>
