<template>
  <div class="task-input my-list">
    <input v-model="title" placeholder="Название задачи" type="text">
    <button @click="onAddTask">добавить</button>
  </div>
</template>

<script lang="ts">
import { ref } from 'vue'

export default {
  emits: {
    onAddTask({ title }) {
      if(title === '') {
        alert('мне че пустую строку в задачу записать чтоли')
        return true
      }
      return false
    }
  },
  setup(props, { emit }) {
    const title = ref('')

    const onAddTask = () => {
      emit('onAddTask', { title: title.value })
    }

    return {
      title,
      onAddTask
    }
  }
}
</script>
