<template>
  <div>
    <h1 class=" font-extrabold text-center text-3xl text-red-900">Home Page</h1>
  </div>
  <div class=" m-5 ">
        <form class=" text-center " action="" @submit.prevent="addTodo">
            <input 
            class=" border-2 w-[300px] h-9 p-3 m-4"  
            type="text" 
            placeholder="Enter your Todo"
            v-model="todoObject.text"
            required>
            <br>
            <input 
            class=" border-2 w-[300px] h-9 p-3 m-4" 
            type="date" 
            placeholder="from"
            v-model="todoObject.from"
            required>
            <input 
            class=" border-2 w-[300px] h-9 p-3 m-4" 
            type="date" 
            placeholder="to"
            v-model="todoObject.to"
            required>
            <br>
            <input class=" text-white p-3 px-5 rounded-md bg-red-900" type="submit" value="Add">

        </form>
    </div>
</template>

<script setup>

import { onMounted, ref } from 'vue';
const todoList = ref([]);
const todoObject = ref({
    id : "",
    text : "",
    from : "",
    to : "",
    createdAt : "",
}); 

//Methods


//Ad Todo
const addTodo = () =>{
    todoObject.value.id = todoList.value.length +1;
    todoObject.value.createdAt = new Date();
    todoList.value.push(todoObject.value);
    addToLocalSt();
    alert("Todo was added successfully!");
    todoObject.value = {
        id : "",
        text : "",
        from : "",
        to : "",
        createdAt : "",
    };
};

//Set to local storage
const addToLocalSt = () =>{
    localStorage.setItem('todos', JSON.stringify(todoList.value));
};

//Update Todos List
const updateTodos = ()=>{
    if (localStorage.getItem('todos')){
        todoList.value = JSON.parse(localStorage.getItem('todos'));
    }
};

//Hooks

onMounted(() =>{
    updateTodos();
})

</script>

<style lang="scss" scoped>

</style>