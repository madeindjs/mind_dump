<template>
  <p>
    <span class="logDate">{{ log.date.slice(0, 16) }}</span>
    <span class="logContent">{{ log.content }}</span>
    <span class="logTag">@home</span>
  </p>
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
p {
  margin-top: 0px;
  margin-bottom: 0px;
}
span.logDate {
  color: gray;
  margin-right: 1rem;
}
span.logContent {
  margin-right: 1rem;
}
span.logTag {
  color: yellow;
}
</style>