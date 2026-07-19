<script setup lang="ts">
const todos = ref<{id: number, text: string}[]>([{id: 1, text: '買い物'}, {id: 2, text: '掃除'}])

function addTodo() {
    const id = todos.value.reduce((a, b) => Math.max(a, b.id), 0) + 1
    todos.value.push({id: id, text: ""})
}

function removeTodo(id: number) {
    todos.value = todos.value.filter(todo => todo.id !== id)
}
</script>

<template>
    <button @click="addTodo">追加</button>
    <div v-for="(todo, index) in todos" :key="todo.id">
        <input type="text" v-model="todo.text" />
        <button @click="removeTodo(todo.id)">削除</button>
    </div>
</template>

<style scoped>
</style>
