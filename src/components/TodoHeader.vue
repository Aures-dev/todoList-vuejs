<script setup>
import { ref, watch } from "vue";

const emit = defineEmits(['addNotif', 'update'])
const newTask = ref();
function taskSending() {
    emit('addNotif', newTask.value);
    newTask.value = '';
}
function verif() {
    if (newTask.value != undefined)
        taskSending()
    else
        alert("Veuilez bien remplir")
}




const loadUpdateItem = ref({})
// eslint-disable-next-line no-unused-vars
const props = defineProps({
    updateItem:Object
})
watch(()=>props.updateItem, (newTask) => loadUpdateItem.value = newTask)


//stock la nouvelle valeur
const modif= ref("")
function recup(e) {
    modif.value= e.target.value;
    console.log(e.target.value);
    
}
//envoi à todolist la modification
let uptache = ref()
function envoiUpdateTache() {
    uptache.value = {id: loadUpdateItem.value.id, content: modif.value, cheked: false};
    emit('update', uptache.value);
    console.log("updating",uptache.value);
    
    loadUpdateItem.value = {};
}

</script>

<template>
    <div class="content">
        <h1 class="title is-1">My TodoList App</h1>
        <form @submit.prevent>
            <fieldset v-if="!updateItem.content">
                <input v-model="newTask" type="text" class="input is-success" placeholder="add task" required>
                <button @click="verif" class="button is-success">Add Task</button>
            </fieldset>
            <fieldset v-else>
                <input :value="loadUpdateItem.content" class="input is-warning" @input="recup">
                <button class="button is-warning" @click="envoiUpdateTache">Modify Task</button>
            </fieldset>
        </form>
    </div>
</template>

<style scoped>
.content{
    display: flex;
    justify-content: center;
    align-items: center;
    flex-direction: column;
    gap: 3em;
    margin-top: 3em;
}
fieldset{
    display: flex;
    gap: 3px;
}
button:active{
    color: white;
}
</style>