<template>
  <div class="album py-5 bg-light">
    <div class="container">
      <div class="row mb-2">
        <div class="col-md-12">
          <div class="card mb-12 shadow-sm">
            <div class="card-body">
              <form @submit.prevent="addNewToDos">
                <div class="form-group">
                  <input
                    type="text"
                    class="form-control"
                    id="new_todo"
                    placeholder="Enter new todo...."
                    v-model="newToDo"
                  />
                </div>

                <button
                  type="button"
                  @click="markAllComplete"
                  class="btn btn-default mr-2"
                >Mark All Complete</button>
                <button type="submit" class="btn btn-primary">ADD NEW TODO</button>
              </form>
            </div>
          </div>
        </div>
      </div>
      <div class="row">
        <div class="col-md-8">
          <div v-for="(todo, index) in todos" :key="index" class="card mb-8 shadow-sm icon">
            <div class="card-body">
              <h3 :class="{ done: todo.done }" @click="addLineThrough(todo)">{{todo.content}}</h3>
              <button type="button" @click="removeTodo(index)" class="btn btn-danger">Remove</button>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import { ref } from "vue";

export default {
  name: "HelloWorld",
  setup() {
    // declare data objects as refs
    const newToDo = ref("");
    const todos = ref([]);
    // declare submit function
    function addNewToDos() {
      todos.value.push({
        id: Date.now(),
        done: false,
        content: newToDo.value,
      });
      newToDo.value = "";
    }

    // add line through class
    function addLineThrough(todo) {
      todo.done = !todo.done;
    }

    // remove todo
    function removeTodo(index) {
      todos.value.splice(index, 1);
    }

    // mark all as completed
    function markAllComplete() {
      todos.value.forEach((todo) => (todo.done = true));
    }

    return {
      newToDo,
      todos,
      addNewToDos,
      addLineThrough,
      removeTodo,
      markAllComplete,
    };
  },
};
</script>

<style scoped>
.done {
  text-decoration: line-through;
}
.icon {
  cursor: pointer;
}
</style>