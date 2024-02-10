<template>
    <div>
        <h1 class=" font-extrabold text-center text-3xl text-red-900">Todos</h1>
    </div>
    <div class=" p-16">
        <table class=" border-2 w-full ">
            <thead class=" border-2 text-xl font-bold text-center">
                <tr>
                    <td>Task</td>
                    <td>From</td>
                    <td>To</td>
                    <td>Created At</td>
                    <td>Action</td>
                </tr>
            </thead>
            <tbody class="  text-sm text-center ">
                <tr v-for="(todo, index) in todoList" :key="todo.id" class="border-2" :style="`${todo.isCompleted ? 'background : #71c278' : 'background : transparent'}`">
                   <td>{{ todo.text }}</td> 
                   <td>{{ todo.from }}</td>
                   <td>{{ todo.to }}</td>
                   <td>{{ new Date(todo.createdAt).toLocaleDateString() }}</td>
                   <td>
                    <div>
                        <button class=" m-2 p-2 bg-green-900 text-white rounded-md" @click="completed(todo)">Completed</button>
                        <button class=" m-2 p-2 bg-red-900 text-white rounded-md" @click="deleteTodo(index)">Delete</button>
                    </div>
                   </td>
                </tr>
            </tbody>
        </table>
    </div>
</template>

<script setup>
import { onMounted, ref } from 'vue';

const todoList = ref([]);

// Methods
const updateTodo = () =>{
    if(localStorage.getItem("todos")){
        todoList.value = JSON.parse(localStorage.getItem("todos"));
    }
    console.log(todoList.value);
};

const deleteTodo = (index) =>{
    todoList.value.splice(index, 1);
    addToLocalSt();
};

const addToLocalSt = () =>{
    localStorage.setItem("todos", JSON.stringify(todoList.value));
};

const completed = (todo) =>{
    todo.isCompleted = ! todo.isCompleted ;
    addToLocalSt();
}

// Hooks
onMounted(() =>{
    updateTodo();
})

</script>

<style lang="scss" scoped>


</style>