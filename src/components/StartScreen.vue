<template>
  <div class="alert">
    <h3>Are you ready?</h3>
    <button class="btn" v-on:click="$emit('on-start')">
      Start
    </button>
  </div>
</template>

<script>
export default {};
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
