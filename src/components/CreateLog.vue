<template>
  <form @submit.prevent="submit">
    <input type="text" v-model="content" />
    <input type="submit" value="create" v-if="content">
  </form>
</template>

<script>
export default {
  name: "CreateLog",
  data() {
    return {
      content: null
    };
  },
  methods: {
    submit: function() {
      if (!this.content) return
      this.$emit("create", this.content)
    }
  }
};
</script>