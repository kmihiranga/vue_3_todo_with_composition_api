<template>
  <h1>ToDo List</h1>
  <form @submit.prevent="addNewToDos">
    <input type="text" placeholder="Enter title...." />
    <button type="submit">Add ToDo</button>
  </form>
</template>

<script>
export default {
  name: "HelloWorld",
  setup() {
    const newToDo = ref("");
    const todos = ref([]);

    function addNewToDos() {
      todos.value.push({
        id: Date.now(),
        done: false,
        content: newToDo.value,
      });
    }
  },
};
</script>
