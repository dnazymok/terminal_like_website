<template>
  <div id="app" v-on:click="focus()">
    <Terminal ref="terminal"/>
  </div>
</template>

<script>
import Terminal from './components/Terminal.vue'

export default {
  name: 'App',
  components: {
    Terminal
  },
  methods: {
    focus: function () {
      this.$refs.terminal.$refs.prompt.focus()
    }
  }
}
</script>

<style>


html, body {
  height: 100%;
  width: 100%;
  margin: 0;
}

#app {
  font-family: 'Fira Code', monospace;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  background: #2b2b2b;
  font-size: 16px;
  font-weight: bold;
  height: 100%;
  width: 100%;
  line-height: 1.35rem;
  color: lightgray;
}

.command {
  color: #CB772F;
}

.developer_name {
  color: #dcc457;
}

.contact_link {
  color: #A5C25C;
}

.contact_link:hover {
  color: gray;
}

.inspired_link {
  color: #9876AA;
}

.inspired_link:hover {
  color: gray;
}

.welcome_border {
  color: #808080
}
</style>
