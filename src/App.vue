<template>
  <div id="app" class="container">
    <h1>Mind Dump</h1>
    <p>Export all your thoughts and let Natural Language Processing <a href="https://spacy.io/" rel="nofollow">Spacy</a> organize them.</p>
    <CreateLog @create="onCreateThought"/>
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
    onCreateThought: function(content) {
      const data = new FormData();
      data.append('content', content)
      
      axios.post('http://127.0.0.1:5000/thoughts/', data)
        .then(() => this.loadThoughts())
    },
  }
}
</script>
