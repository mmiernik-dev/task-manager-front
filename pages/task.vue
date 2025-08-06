<template>
  <div class="p-6">
    <h1 class="text-2xl font-bold mb-4">Lista zadań</h1>

    <div v-if="pending">Ładowanie...</div>
    <div v-else-if="error">Błąd ładowania: {{ error.message }}</div>
    <ul v-else class="space-y-2">
      <li
        v-for="task in tasks"
        :key="task.id"
        class="p-4 bg-white shadow rounded border"
      >
        <p class="font-semibold">{{ task.title }}</p>
        <p class="text-gray-600 text-sm">{{ task.description }}</p>
      </li>
    </ul>
  </div>
</template>

<script setup>
const { data: tasks, pending, error } = await useFetch('http://localhost:8000/tasks')
</script>