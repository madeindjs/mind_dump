<template>
  <div id="app" class="container">
    <h1>Mind Dump</h1>
    <p>Export all your thoughts and let Natural Language Processing <a href="https://spacy.io/" rel="nofollow">Spacy</a> organize them.</p>
    <CreateLog @create="onCreateThought"/>
    <div class="loader" v-if="loading"></div>
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
      thoughts: [],
      loading: false
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
      this.loading = true
      axios.get('http://127.0.0.1:5000/thoughts/')
        .then(res => this.thoughts = res.data)
        .catch(e => console.error(e))
        .finally(() => this.loading = false)
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
<style>
.loader,
.loader:before,
.loader:after {
  border-radius: 50%;
  width: 2.5em;
  height: 2.5em;
  -webkit-animation-fill-mode: both;
  animation-fill-mode: both;
  -webkit-animation: load7 1.8s infinite ease-in-out;
  animation: load7 1.8s infinite ease-in-out;
}
.loader {
  color: #ffffff;
  font-size: 10px;
  margin: 80px auto;
  position: relative;
  text-indent: -9999em;
  -webkit-transform: translateZ(0);
  -ms-transform: translateZ(0);
  transform: translateZ(0);
  -webkit-animation-delay: -0.16s;
  animation-delay: -0.16s;
}
.loader:before,
.loader:after {
  content: '';
  position: absolute;
  top: 0;
}
.loader:before {
  left: -3.5em;
  -webkit-animation-delay: -0.32s;
  animation-delay: -0.32s;
}
.loader:after {
  left: 3.5em;
}
@-webkit-keyframes load7 {
  0%,
  80%,
  100% {
    box-shadow: 0 2.5em 0 -1.3em;
  }
  40% {
    box-shadow: 0 2.5em 0 0;
  }
}
@keyframes load7 {
  0%,
  80%,
  100% {
    box-shadow: 0 2.5em 0 -1.3em;
  }
  40% {
    box-shadow: 0 2.5em 0 0;
  }
}
</style>