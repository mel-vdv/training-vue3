<template>
    <h1>{{ titre }}</h1>

    <p ref="pDOM">....</p>

    <form @submit.prevent="addTask">
        <input type="text" v-model="newTask"><!-- AU LIEU DE v-model : :value="newTASK" ET @input="(e)=>{newTask = e.target.value}"  -->
        <button v-bind:type="submit">Add a new task</button>
    </form>

   

    <br><br>

    <template v-if="todos.length">
  

        <div v-for="todo in todosFiltered" :key="todo.id" class="itemtache">
            <input type="checkbox" name="todo.id" id="todo.id" v-model="todo.done">
            <div v-bind:class="todo.done ? 'barre': ''">{{ todo.text }}</div>
            <img src="./../assets/trash.svg" alt="trash" v-on:click="trash(todo.id)">
        </div>
       
        <br><br>

        <button @click="() => hideCompleted = !hideCompleted"><!-- @click ou v-on:click-->
            {{ hideCompleted ? 'Afficher toutes' : 'Masquer les tâches accomplies'  }}
        </button>
    </template>
   
    <p v-else>Aucune tache pour le moment</p>

    <br><br>
    <Secours>contenu parent non vide</Secours>
</template>








<script setup>

import { ref, onMounted, computed } from 'vue';
import Secours from './Secours.vue';

const titre = ref('Les tâches')
const newTask=ref('');
function addTask() {
    todos.value.push({id: id.value++, text: newTask.value, done: false});
    newTask.value = ""

}
const id =ref(0);
const hideCompleted = ref(false);
const todos = ref([{id:0, text: 'test', done: false}])

const todosFiltered = computed(()=> {
    return hideCompleted.value ? todos.value.filter(t => !t.done) : todos.value;
})

const pDOM=ref(null)
onMounted(()=> { pDOM.value.textContent = "chargé ! "})

function trash(id) {
    todos.value = todos.value.filter(t => t.id !== id)
}

</script>






<style scoped>
h1 {
    color: red
}
.barre {
    text-decoration: line-through ;
}
img[alt="trash"] {
    height: 30px;
    width: auto;
}
.itemtache  {
    display: flex;
    align-items: center;
    gap: 15px;
}

</style>