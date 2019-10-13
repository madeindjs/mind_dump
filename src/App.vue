<template>
  <div id="app" class="container">
    <div class="row">
      <div class="column">
        <h1>Log Stuff</h1>
        <CreateLog @create="onCreateLog"/>
        <table>
          <thead>
            <tr>
              <th>hour</th>
              <th>content</th>
            </tr>
          </thead>
          <tbody>
            <LogEntry v-for="(log, index) in logs" :key="index" :log="log" />
          </tbody>
        </table>
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
  methods: {
    onCreateLog: function(log) {
      this.logs.push({
        date: new Date(),
        content: log,
      })
    }
  }
}
</script>
