<template>
  <div id="app" class="container">
    <div class="row">
      <div class="column">
        <h1>Log Stuff</h1>
        <CreateLog @create="onCreateLog"/>
        <ul>
          <li v-for="(log, index) in logs" :key="index">{{ log }}</li>
        </ul>
      </div>
    </div>
  </div>
</template>

<script>
import 'normalize.css'
import 'concrete.css'

import CreateLog from './components/CreateLog'

export default {
  name: 'app',
  data() {
    return {
      logs: []
    } 
  },
  components: {
    CreateLog,
  },
  methods: {
    onCreateLog: function(log) {
      this.logs.push(log)

    }
  }
}
</script>
