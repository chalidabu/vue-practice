<script setup>
import MainInput from '@/components/atoms/MainInput.vue'
import MainButton from '@/components/atoms/MainButton.vue'
import { ref } from 'vue'

const newTask = ref('')
const tasks = ref([])

const addTask = () => {
  if (newTask.value.trim() !== '') {
    tasks.value.push(newTask.value)
    newTask.value = ''

    console.log(tasks.value)
  } else {
    alert('Input tidak boleh kosong!')
  }
}

const removeTask = (index) => {
  tasks.value = tasks.value.filter((_, i) => i !== index)
  console.log('dihapus')
  console.log(tasks.value)
}
</script>

<template>
  <main>
    <div class="container">
      <h1>To Do List</h1>

      <div>
        <MainInput id="newTask" v-model="newTask" placeholder="Add New Task" />
        <MainButton @click="addTask">Add</MainButton>
      </div>

      <ul>
        <li v-for="(task, index) in tasks" :key="index">
          <div>
            {{ task }}
            <MainButton @click="removeTask(index)">Delete</MainButton>
          </div>
        </li>
      </ul>
    </div>
  </main>
</template>

<style scoped>
main {
  display: flex;
  justify-content: center;
}
.container {
  width: 100%;
  max-width: 720px;
  text-align: center;
  padding: 2rem;
}

h1 {
  margin: 2rem;
}
ul {
  text-align: left;
}
li > div {
  display: flex;
  justify-content: space-between;
}
</style>
