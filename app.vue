<template>
  <main>
    <h1>Todo List</h1>
    <p>добавьте новую задачу</p>
    <div class="create-new">
      <TaskInput @onAddTask="addTask"></TaskInput>
    </div>
    <ul class="tasks my-list">
      <li v-for="item in taskList" :key="item.id">
        <Task @onRemove="removeTask(item.id)" @onDone="setDoneTask(item.id)" :model="item"></Task>
      </li>

    </ul>
  </main>
</template>

<script>

import {ref} from 'vue'
import TaskInput from "./components/TaskInput.vue";
import Task from "./components/Task.vue";

export default {
  name: 'App',
  components: {
    Task,
    TaskInput
  },
  setup() {
    const taskList = ref([{id: 0, title: 'example №1', description: '', status: false}])

    const addTask = ({title, description}) => {
      taskList.value = [...taskList.value, {id: taskList.value[taskList.value.length - 1].id + 1, title, status: false}]
    }

    const setDoneTask = (id) => {
      taskList.value = taskList.value.map(x => {
        if(x.id === id)
          x.status = true
        return x
      })
    }

    const removeTask = (id) => {
      taskList.value = taskList.value.filter(x => x.id !== id)
    }

    return {
      taskList,
      addTask,
      removeTask,
      setDoneTask
    }
  }
}
</script>

<style scoped>
  .task-list {
    list-style: none;
  }
</style>