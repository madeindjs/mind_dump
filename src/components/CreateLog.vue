<template>
  <div class="row">
    <div class="column">
      New log
    </div>
    <div class="column">
      <form @submit.prevent="submit">
        <input type="text" v-model="content" />
      </form>
    </div>
  </div>
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
<style>
input, form {
  margin-bottom: 0;
}
</style>