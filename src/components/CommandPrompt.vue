<template>
  <div>
    <span class="user">user</span><span class="tilde">~</span>$
    <input ref="prompt" type="text" v-model="command" v-on:keyup.enter="submit()">
    <span>{{ command }}</span>
    <span class="caret"></span>
  </div>
</template>

<script>
export default {
  name: "CommandPrompt",
  data() {
    return {
      command: ''
    }
  },
  methods: {
    focus() {
      this.$refs.prompt.focus()
    },
    submit() {
      this.$parent.addCommand(this.command)
      this.command = ""
    }
  }
}
</script>

<style>
input {
  width: 0;
  opacity: 0;
  padding: 0;
  border: 0;
}

input:focus + span + .caret {
  background-color: white;
  animation: blink .75s steps(2, start) infinite;
}

.user {
  color: #dcc457;
}

.tilde {
  color: #CB772F;
}

.caret {
  display: inline-block;
  height: 0.75rem;
  width: 0.45rem;
  position: relative;
  top: 0.2rem;
  left: 1px;
  border: 1px solid rgba(white, 0.8);
}

@keyframes blink {
  to {
    visibility: hidden;
  }
}
</style>