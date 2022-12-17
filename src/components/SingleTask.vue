<template>
  <div
    class="task"
    :class="[completed && 'completed']"
    @dblclick="$emit('toggle-handler', id)"
  >
    <p class="taskName">{{ task }}</p>
    <p class="taskTime">{{ time }}</p>
    <button @click="$emit('delete-handler', id)">x</button>
  </div>
</template>

<script>
export default {
  name: "SingleTask",
  props: ["task", "time", "id", "completed"],
  methods: {
    deleteHandler(id) {
      console.log(id);
      this.$emit("delete-handler", id);
    },
  },
};
</script>

<style scoped>
.task {
  width: 100%;
  margin-bottom: 12px;
  padding: 0 12px;
  box-sizing: border-box;
  border-left: 4px solid #ff2828;
  position: relative;
}
.task.completed {
  border-left: 4px solid #008000;
}
.taskName {
  font-weight: 700;
  font-size: 20px;
}
.taskTime {
  color: #222;
  font-weight: 600;
  font-size: 14px;
}
.task button {
  background-color: #ff2828;
  color: #fff;
  border-radius: 5px;
  position: absolute;
  right: 12px;
  top: 50%;
  transform: translateY(-50%);
  cursor: pointer;
  display: grid;
  place-content: center;
}
</style>
