<template>
  <div class="row">
    <!-- <div class="column">{{ log.date.slice(0, 16) }}</div> -->
    <div class="column">
      <p>
        <span
          v-for="(tag, i) in tags"
          :key="i"
        >
          {{ tag.content }}
        </span>
      </p>
      <p>{{ content }}</p>
    </div>
  </div>
</template>

<script>
export default {
  name: "LogEntry",
  props: ["content", "tags", "id"],
  data() {
    return {
      // content: null
    };
  },
};
</script>
<style scoped>
p {
  text-align: justify;
}
</style>