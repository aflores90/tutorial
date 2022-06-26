<template>
  <h1>TODO</h1>
  <input v-model="task" />
  <button @click="handleTask">Agregar tarea</button>
  <ul>
    <li v-for="(item, index) in list" :key="index">
      <span :class="item.finished ? 'finished' : ''">
        {{ item.name }}
      </span>
      <input type="checkbox" @change="handleCheck(index)" :checked="item.finished" />
    </li>
  </ul>
</template>

<script setup>
import { ref } from '@vue/reactivity'

const task = ref('')
const list = ref([
  {
    name: 'Lavar ropa',
    finished: false
  },
  {
    name: 'Tender la cama',
    finished: false
  }
])

const handleTask = () => {
  list.value.push({
    name: task.value,
    finished: false
  })
  task.value = ''
}

const handleCheck = (index) => {
  list.value[index].finished = !list.value[index].finished
}
</script>

<style scoped>
.finished {
  text-decoration: line-through;
}
</style>
