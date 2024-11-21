<script setup>

// eslint-disable-next-line no-unused-vars
const props = defineProps({
    tasks: Array
})

const emit = defineEmits(['deleteNotif', 'updateResponse'])

</script>

<template>
    <ul>
        <li v-for="(task, index) in tasks" :key="index">
            <input type="checkbox" v-model="task.cheked">
            <div class="box" :class="{cheked: task.cheked}">{{ task.content }}</div>
            <button class="button is-danger" @click="() => emit('deleteNotif',task)">Delete</button>
            <button class="button is-success" @click="() => emit('updateResponse',task)">Modify</button>
        </li>
    </ul>
</template>

<style scoped>
.box{
    margin-bottom: 8px;
}
.button{
    margin-bottom: 1.5em;
}
.cheked{
    text-decoration: line-through;
}
</style>