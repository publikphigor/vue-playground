<template>
  <h1>Counter App</h1>
  <div class="counter-container">
    <div class="counter--inner">
      <button @click="decrement" class="prev-btn">-</button>
      <h2>{{ count }}</h2>
      <button @click="increment" class="next-btn">+</button>
    </div>
  </div>
</template>

<script>
export default {
  name: "CounterApp",

  data() {
    return {
      count: 0,
    };
  },

  methods: {
    increment() {
      this.count = this.count + 1;
    },

    decrement() {
      this.count = this.count - 1;
    },
  },
};
</script>

<style scoped>
* {
  padding: 0;
  margin: 0;
}

.counter-container {
  padding: 20px;
  border-radius: 8px;
  border: 4px solid #222;
  max-width: 400px;
  margin: 20px auto;
}

.counter--inner {
  display: flex;
  align-items: flex-end;
  justify-content: center;
  gap: 5px;
}

h2 {
  font-size: 150px;
  font-weight: 300;
  padding: 0;
  margin: 0;
}

button {
  background-color: #222;
  color: #fff;
  padding: 10px 20px;
  font-size: 16px;
  cursor: pointer;
}
</style>
