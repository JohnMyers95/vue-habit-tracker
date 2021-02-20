<template>
  <div class="popup">
    <div class="content">
      <form @submit.prevent="addHabit">
        <div class="title">
          <input type="text" v-model="title" />
        </div>
        <div class="goal">
          <input type="number" v-model="goal" />
        </div>
        <button type="submit">Add</button>
      </form>
    </div>
  </div>
</template>
<script>
export default {
  data: () => {
    return {
      title: "",
      goal: 0,
      progress: 0,
    };
  },
  props: [],
  methods: {
    addHabit() {
      console.log("habbit added!");
      this.$emit("new-habit", {
        title: this.title,
        goal: this.goal,
        progress: this.progress,
      });
      this.$parent('close');
    },
  },
};
</script>
<style scoped>
.popup {
  display: block;
  position: fixed;
  z-index: 1;
  padding-top: 100px;
  left: 0;
  top: 0;
  width: 100%;
  height: 100%;
  overflow: auto;
  background-color: rgb(0, 0, 0);
  background-color: rgba(0, 0, 0, 0.4);
  transition: 0.5s;
}
.content {
  background-color: white;
  display: inline-block;
  padding: 30px;
  box-shadow: 2px 2px 1px 1px black;
}
</style>
