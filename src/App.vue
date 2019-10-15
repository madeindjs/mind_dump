<template>
  <div id="app" class="container">
    <h1>Log Stuff</h1>
    <CreateLog @create="onCreateLog"/>
    <hr>

    <div class="column" v-for="(thought, index) in thoughts" :key="index">
      <Thought
        :id="thought.id"
        :content="thought.content"
        :tags="thought.tags"
      />
      <hr>
    </div>
  </div>
</template>

<script>
import 'normalize.css'
import 'concrete.css'

const axios = require('axios');

import CreateLog from './components/CreateLog'
import Thought from './components/Thought'

export default {
  name: 'app',
  data() {
    return {
      thoughts: []
    } 
  },
  components: {
    CreateLog,
    Thought,
  },
  mounted() {
    this.loadThoughts()
  },
  methods: {
    loadThoughts: function() {
      axios.get('http://127.0.0.1:5000/thoughts/')
        .then(res => this.thoughts = res.data)
        // .catch(e => console.error(e))
    },
    onCreateLog: function(content) {
      const now = new Date
      const date = now.toISOString()

      this.thoughts.push({
        timestamp: new Date().getTime(),
        date,
        content,
      })
      localStorage.setItem('logs', JSON.stringify(this.thoughts));
    },
  }
}
</script>
