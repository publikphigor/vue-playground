<template>
  <p>Reaction time: {{ results }}ms.</p>
  <p class="rank">{{ rank }}</p>
</template>

<script>
export default {
  props: ["results"],
  data() {
    return {
      rank: null,
    };
  },
  mounted() {
    if (this.results < 250) {
      this.rank = "Ninja Fingers";
    } else if (this.results < 400) {
      this.rank = "Rapid Reflexes";
    } else {
      this.rank = "Small pace...";
    }
  },
};
</script>

<style scoped>
p {
  font-size: 16px;
  font-weight: 700;
}
.rank {
  font-size: 1.4rem;
  font-weight: bold;
  color: #0fa487;
}
</style>
