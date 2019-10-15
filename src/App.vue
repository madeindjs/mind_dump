<template>
  <div id="app" class="container">
    <div class="row">
      <div class="column">
        <h1>Log Stuff</h1>
        <CreateLog @create="onCreateLog"/>
        <hr>
        <LogEntry v-for="(log, index) in logs.reverse()" :key="index" :log="log" />
      </div>
    </div>
  </div>
</template>

<script>
import 'normalize.css'
import 'concrete.css'

import CreateLog from './components/CreateLog'
import LogEntry from './components/LogEntry'

export default {
  name: 'app',
  data() {
    return {
      logs: []
    } 
  },
  components: {
    CreateLog,
    LogEntry,
  },
  mounted() {
    this.logs = JSON.parse(localStorage.getItem('logs')) || []
  },
  methods: {
    onCreateLog: function(content) {
      const now = new Date
      const date = now.toISOString()

      this.logs.push({
        timestamp: new Date().getTime(),
        date,
        content,
      })

      localStorage.setItem('logs', JSON.stringify(this.logs));
    },
  }
}
</script>
