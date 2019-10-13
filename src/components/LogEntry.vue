<template>
  <tr>
    <td>{{ log.date.toISOString() }}</td>
    <td>{{ log.content }}</td>
  </tr>
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
