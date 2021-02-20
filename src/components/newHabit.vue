<template>
    <div class="popup">
        <form @submit.prevent="addHabit">
        <div class="title">
            <input type="text" v-model="title">
        </div>
        <div class="goal">
            <input type="number" v-model="goal">
        </div>
        <button type="submit">Add</button>
        </form>
    </div>
</template>
<script>
export default {
    data: () => {
        return {
            title: "",
            goal: 0,
            progress: 0
        }
    },
    props: [],
    methods: {
        addHabit() {
            console.log('habbit added!');
            this.$emit('new-habit', {'title':this.title, 'goal':this.goal, 'progress':this.progress});
        }
    }
}
</script>
<style scoped>
.popup {
    display:flex;
    z-index: -1;
    background-color:white;
}
</style>