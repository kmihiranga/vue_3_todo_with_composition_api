<template>
  <div class="album py-5 bg-light">
    <div class="container">
      <div class="row">
        <div class="col-md-12">
          <div class="card mb-12 shadow-sm">
            <div class="card-body">
              <form>
                <div class="form-group">
                  <input
                    type="text"
                    class="form-control"
                    id="new_todo"
                    placeholder="Enter new todo...."
                    v-model="newToDo"
                  />
                </div>
                <button type="submit" class="btn btn-primary">ADD NEW TODO</button>
              </form>
            </div>
          </div>
        </div>
      </div>
      <div class="row">
        <div class="col-md-12">
          <div v-for="(todo, index) in todos" :key="index" class="card mb-8 shadow-sm">
            <div class="card-body">
              <h3>{{todo.content}}</h3>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "HelloWorld",
  setup() {
    const newToDo = ref("");
    // const todos = ref([]);
    function addNewToDos() {
      todos.value.push({
        id: Date.now(),
        done: false,
        content: newToDo.value,
      });
    }
    return {
      newToDo,
      todos,
      addNewToDos,
    };
  },
};
</script>
