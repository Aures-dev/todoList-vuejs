<script setup>
import TodoHeader from "./TodoHeader.vue";
import TodoItem from "./TodoItem.vue";
import TodoFooter from "./TodoFooter.vue";
import { ref } from "vue";


let taskId = 1;
let count = 0;
const tasks = ref([
    {id:taskId++, content:"Default task", cheked:false}
])

function addTask(elem) {
    return tasks.value.push({id: taskId++, content: elem, cheked:false})
}
function deleteTask(param) {
    return tasks.value = tasks.value.filter((test) => test !== param)
}

const updateItem = ref({})
function updateTodo(param) {
    updateItem.value = param;
}



function miseAjour(e) {
    tasks.value.forEach(element => {
        if (element.id === e.id) {
            element.content = e.content
        }
    }

    )
}

</script>

<template>
    <TodoHeader @addNotif="addTask" :updateItem="updateItem" @update="miseAjour"/>
    <TodoItem :tasks="tasks" @deleteNotif="deleteTask" @updateResponse="updateTodo"/>
    <TodoFooter :count="count"/>
</template>

<style scoped>

</style>