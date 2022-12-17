<template>
  <h1>To-do Application</h1>
  <div
    class="addTodo"
    @delete-handler="$emit('delete-handler')"
    @toggle-handler="$emit('toggle-handler')"
  >
    <form @submit.prevent="$emit('add-new-todo', newTodo)">
      <input
        type="text"
        v-model="newTodo.task"
        placeholder="Add a new todo..."
      />
      <input v-model="newTodo.time" type="text" placeholder="Time" />
      <input type="checkbox" v-model="newTodo.completed" />
      <button>Add Todo</button>
    </form>
  </div>
  <div class="todos">
    <h2 v-if="todos.length === 0">There are no todos, add a new todo above.</h2>
    <SingleTask
      v-for="(todo, i) in todos"
      :task="todo.task"
      :time="todo.time"
      :completed="todo.completed"
      :key="i"
      :id="i"
    />
  </div>
</template>

<script>
import SingleTask from "./SingleTask";

export default {
  name: "TaskApp",
  components: {
    SingleTask,
  },
  props: ["todos"],
  emits: ["toggle-handler", "delete-handler"],
  data() {
    return {
      newTodo: {
        task: "",
        time: "",
        completed: false,
      },
    };
  },
};
</script>

<style scoped>
.todos {
  width: 90%;
  max-width: 500px;
  margin: 30px auto;
  border: 2px solid aqua;
  box-sizing: border-box;
  overflow: hidden;
}
.todos h2 {
  font-size: 16px;
  padding: 0 12px;
}
.addTodo {
  width: 90%;
  max-width: 500px;
  margin: 30px auto;
}
form {
  display: flex;
  align-items: center;
  flex-wrap: wrap;
  gap: 2%;
}
form input[type="text"] {
  width: 40%;
  padding: 10px;
  font-size: 20px;
}
form input[type="checkbox"] {
  width: 20px;
  height: 20px;
}
form button {
  margin-top: 12px;
  padding: 10px 30px;
  color: #fff;
  background-color: #222;
  cursor: pointer;
}
form button:hover {
  filter: brightness(125%);
}
</style>
