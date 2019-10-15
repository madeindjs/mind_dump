<template>
  <div class="row">
    <div class="column">{{ log.date.slice(0, 16) }}</div>
    <div class="column">
      <input type="text" :value="log.content">
    </div>
  </div>
</template>

<script>
export default {
  name: "LogEntry",
  props: ["log"],
  data() {
    return {
      content: null
    };
  },
  methods: {
    submit: function() {
      this.$emit("create", this.content);
    }
  }
};
</script>
<style scoped>
input {
  border: none;
  margin-bottom: 0;
}
</style>