<template>
  <article>
    <p v-html="contentWithStrongs()"></p>
  </article>
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
  methods: {
    contentWithStrongs() {
      let content = this.content;

      this.tags.forEach(tag => {
        content = content.replace(tag.content, `<strong class="${tag.label}">${tag.content}</strong>`)
      })

      return content;
    }
  }
};
</script>
<style>
p {
  text-align: justify;
}
ul {
  list-style: none;
  padding-left: 0;
}
li {
  display: inline
}
strong.MISC{
  color: darkblue;
}
strong.PER{
  color: darkred;
}
strong.ORG{
  color: darkorange;
}
strong.LOC{
  color: darkorchid;
}
</style>