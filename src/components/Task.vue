<template>
  <div
    @dblclick="$emit('toggle-reminder', task.id)"
    :class="[task.reminder ? 'reminder' : '', 'task']"
  >
    <h3>
      {{ task.text }}
      <button @click="$emit('delete-task', task.id)" class="fas">X</button>
    </h3>
    <p>{{ task.day }}</p>
  </div>
</template>

<script>
export default {
  name: "Task",
  props: {
    task: Object,
  },
};
</script>


<style scoped>
.fas {
  color: red;
}
.task {
  background-color: purple;
  color: white;
  margin: 5px;
  padding: 10px 20px;
  cursor: pointer;
}
</style>