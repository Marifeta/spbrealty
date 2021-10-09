<template>
  <div id="app">
    <List />
    <div>

    </div>
  </div>
</template>

<script>
import List from "./pages/List";

export default {
  name: 'App',
  components: {
    List,
  }
}
</script>

<style lang="sass">
@import "assets/main.sass"
*
  box-sizing: border-box
  outline: none
  padding: 0
  margin: 0
  border: none
  font-family: PT Sans
html
  height: 100%
body
  background-color: $body_bg
  min-width: 340px
  height: 100%
#app
  height: 100%
</style>
