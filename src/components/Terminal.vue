<template>
  <div class="terminal">
    <div v-for="cmd in commands" :key="cmd.index">
      <CommandLine :cmd="cmd"/>
    </div>
    <CommandPrompt ref="prompt"/>
  </div>
</template>

<script>
import CommandPrompt from './CommandPrompt'
import CommandLine from './CommandLine'

export default {
  name: "Terminal",
  components: {
    CommandPrompt,
    CommandLine
  },
  data() {
    return {
      commands: ["welcome"],
      cmd_list: {
        "welcome": this.welcome,
        "help": this.help,
        "clear": this.clear,
        "about": this.about,
        "contact": this.contact,
        "inspired_by": this.inspired_by,
      }
    }
  },
  mounted() {
    this.$refs.prompt.focus()
  },
  methods: {
    addCommand(command) {
      this.commands.push(command)
    },
    run(command) {
      command = command.trim()
      if (command in this.cmd_list) {
        return this.cmd_list[command]()
      } else {
        return [`<p>Command <span class="command">${command}</span> not found</p>`]
      }
    },
    welcome() {
      return [
        "<p class='welcome_border'>*======================================" +
        "==============================================================*</p>",
        "<p>Hey! I'm <span class='developer_name'>Dmitriy Nazymok</span>, and this site is " +
        "my attempt to do something cool in Vue.js.</p>",
        "<p>Try print <span class='command'>`help`</span></p>",
        "<p class='welcome_border'>*======================================" +
        "==============================================================*</p>"
      ]
    },
    help() {
      return [
        "<p>List of available commands:<p/>",
        "<span class='command'>about</span> \t\t <i>get more info about me</i>",
        "<span class='command'>contact</span> \t <i>contact me</i>",
        "<span class='command'>clear</span> \t\t <i>clear terminal</i>",
        "<span class='command'>inspired_by</span> \t <i>get cool sites</i>",
      ]
    },
    about() {
      return [
        "<p>My name is Dmitriy, I'm a Python developer from Ukraine. ",
        "<p>I love programming, technology and everything related to it. Hope you like this app :)<p/>"
      ]
    },
    contact() {
      return [
        "<a class='contact_link' href='https://github.com/dnazymok'>GitHub</a>",
        "<a class='contact_link' href='https://www.linkedin.com/in/dnazymok/'>Linkedin</a>",
        "<a class='contact_link' href='https://t.me/dnazymok'>Telegram</a>",
        "<p>dnazymok@gmail.com</p>"
      ]
    },
    clear() {
      this.commands = []
    },
    inspired_by() {
      return [
        "<a class='inspired_link' target='_blank' rel='noopener noreferrer' href='https://metarhia.com/'>Metarhia</a>",
        "<a class='inspired_link' target='_blank' rel='noopener noreferrer' href='https://chewingcode.com/'>Vuebuntu</a>",
        "<a class='inspired_link' target='_blank' rel='noopener noreferrer' href='http://codebyte.re/'>Codebyte</a>",
      ]
    }
  }
}
</script>

<style scoped>
.terminal {
  background: #2b2b2b;
  padding: 0.85rem;
}
</style>