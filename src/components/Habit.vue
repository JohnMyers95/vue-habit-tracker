<template>
    <div class="habit" @click="addProgress">
        <div class="title">
            {{habit.title}}
        </div>
        <div class="progress">
           <h1>{{this.progress}} / {{habit.goal}} </h1>
        </div>
    </div>
</template>
<script>
export default {
    data: () => {
        return {
            progress: 0,
        }
    },
    props: {
        habit: {
            type: Object,
            required: true
        }
    },
    methods: {
        addProgress() {
            if(this.progress < this.habit.goal) {
                this.progress++;
            }
        }
    },
    created: () => {

    }
}
</script>

<style scoped>
.habit {
    display: grid;
    grid-template-columns: 1fr;
    grid-template-rows: 1fr 9fr;
    border-radius: 30px;
    background-color:palegoldenrod;
    aspect-ratio: 1/1;
    border: 1px solid black;
    box-shadow: 4px 4px 2px 1px #8a8a8a;
}
.title{
    display:flex;
    justify-content: center;
}
</style>