<template>
  <div class="task">
    <div class="content">
      <h4>{{model.title}}</h4>
    </div>
    <button v-if="!model.status" @click="emitOnDone">сделано</button>
    <button @click="emitOnRemove" class="delete">удалить</button>
  </div>
</template>

<script lang="ts">
export default {
  props: {
    model: {
      required: true,
      default: {
        id: 0,
        title: 'sasda',
        status: false
      }
    }
  },
  setup(props, {emit}) {
    const emitOnDone = () => {
      emit('onDone')
    }
    const emitOnRemove = () => {
      emit('onRemove')
    }

    return {
      emitOnDone,
      emitOnRemove
    }
  }
}
</script>

