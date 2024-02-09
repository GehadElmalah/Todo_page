<template>
    <div class=" w-full text-center p-6 mb-4 bg-slate-900">
        <ul class=" inline-flex align-middle gap-10">
            <li class=" text-lg text-neutral-50 hover:text-orange-200">
                <router-link :to="{name: 'home'}">Home Page</router-link>
            </li>
            <li class=" text-lg text-neutral-50 hover:text-orange-200">
                <router-link :to="{name: 'todo'}">Todos</router-link>
            </li>
        </ul>
    </div>
</template>

<script setup>

</script>

<style lang="scss" scoped>

</style>