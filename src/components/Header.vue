<template>
  <header>
    <h1>{{ title }}</h1>
    <Button text="Add Task" color="green" />
    <Button text="Update Task" color="blue" />
  </header>
</template>

<script>
import Button from "./Button";

export default {
  name: "Header",
  props: {
    title: {
      type: String,
      default: "Hello default"
    }
  },
  components: {
    Button
  }
};
</script>

<style>
header {
  display: flex;
  justify-content: space-between;
  align-items: center;
}
</style>
