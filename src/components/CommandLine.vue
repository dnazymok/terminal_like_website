<template>
  <span class="user">user</span><span class="tilde">~</span>$
  <span>{{ cmd }}</span>
  <ul :class="cmd">
    <li v-for="(item, index) in response" :key="index">
      <pre v-html="item"></pre>
    </li>
  </ul>
</template>

<script>
export default {
  name: "CommandLine",
  props: [
    "cmd"
  ],
  data() {
    return {
      response: this.$parent.run(this.cmd)
    }
  }
}
</script>
<style scoped>
ul {
  list-style-type: none;
  padding: 0;
}

pre {
  margin: 0
}

</style>