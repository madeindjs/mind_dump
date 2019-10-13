<template>
  <div id="app" class="container">
    <div class="row">
      <div class="column">
        <h1>Log Stuff</h1>
        <CreateLog @create="onCreateLog"/>
        <LogEntry v-for="(log, index) in logs" :key="index" :log="log" />
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
    onCreateLog: function(log) {
      const now = new Date

      this.logs.push({
        date: now.toISOString(),
        content: log,
      })

      localStorage.setItem('logs', JSON.stringify(this.logs));
    },
  }
}
</script>
