<template>
  <div>
    <form @submit.prevent="submit">
      <input type="text" v-model="content" />
      <input type="submit" value="Add" v-if="content" />
    </form>
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
    submit: function () {
      this.$emit('create', this.content)
    }
  }
};
</script>
