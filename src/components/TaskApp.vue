<template>
  <h1>To-do Application</h1>
  <div class="addTodo">
    <form @submit.prevent="addNewTodo">
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
      :deleteHandler="deleteTodo"
      :toggleHandler="toggleStatus"
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
  data() {
    return {
      newTodo: {
        task: "",
        time: "",
        completed: false,
      },
      todos: [
        {
          task: "Build a todo app with vue",
          time: "22:00PM",
          completed: false,
        },
        {
          task: "Build an e-commerce app with vue",
          time: "22:00PM",
          completed: false,
        },
        {
          task: "Implement vue router",
          time: "22:00PM",
          completed: false,
        },
        {
          task: "Learn Pinia/Vuex",
          time: "22:00PM",
          completed: false,
        },
        {
          task: "Watch NetNinja course",
          time: "22:00PM",
          completed: false,
        },
      ],
    };
  },

  methods: {
    addNewTodo() {
      if (this.newTodo.task === "" || this.newTodo.time === "")
        return alert("Fill the gaps!");

      this.todos = [...this.todos, { ...this.newTodo }];
      this.newTodo = {
        task: "",
        time: "",
        completed: false,
      };
    },
    deleteTodo(id) {
      this.todos = this.todos.filter((_, i) => i !== id);
    },
    toggleStatus(id) {
      const updatedTodos = this.todos.map((todo, i) => {
        if (i !== id) return todo;
        return { ...todo, completed: !todo.completed };
      });
      console.log(updatedTodos);

      //this.todos = updatedTodos;
    },
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
