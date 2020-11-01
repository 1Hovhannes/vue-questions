<template>
  <div class="alert">
    <h2>{{ text }}</h2>
    <hr />
    <button class="btn" v-on:click="$emit('on-next')">Continue</button>
  </div>
</template>

<script>
export default {
  props: ['type', 'text']
};
</script>

<style scoped>
.alert {
  text-align: center;
  background: #cccccc;
}

.btn {
  background-color: green;
  color: white;
}

h3,
.btn {
  margin: 20px 0;
}
</style>
