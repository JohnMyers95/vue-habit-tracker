<template>
  <div class="popup">
    <div class="content">
      <div class="topBar">
        <div></div>
        <div class="closeButton" @click="close">X</div>
      </div>
      <form @submit.prevent="addHabit">
        <div class="title">
          <input type="text" placeholder="Drink Water?" v-model="title" />
        </div>
        <div class="goal">
          <input type="number" v-model="goal" />
        </div>
        <button type="submit">Add Habit</button>
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
      this.$parent("close");
    },
    close() {
      this.$emit('close');
    }
  },
};
</script>
<style scoped>
.popup {
  display: block;
  position: fixed;
  z-index: 1;
  padding-top: 60px;
  left: 0;
  top: 0;
  width: 100%;
  height: 100%;
  overflow: auto;
  background-color: rgba(0, 0, 0, 0.4);
  transition: all 0.1s linear;
}
.content {
  background-color: white;
  display: inline-block;
  box-shadow: 2px 2px 1px 1px black;
}
.topBar {
  height: 40px;
  border-bottom: 2px solid black;
  display: grid;
  grid-template-columns: 5fr 1fr;
}
.closeButton {
  display: flex;
  align-items: center;
  justify-content: center;
  border-left: 2px solid black;
  font-weight: bold;
}
input {
  padding: 10px;
  font-size: 1.4em;
  font-weight: bold;
  box-shadow: 2px 2px 1px 0px black;
  margin: 5px;
}
form {
  display: grid;
  padding: 10px 30px 30px;
}
button {
  font-size: 1.3em;
  padding: 10px;
  margin: 10px;
  appearance: none;
  box-shadow: 2px 2px 1px 0px black;
  font-weight: bold;
}
</style>
