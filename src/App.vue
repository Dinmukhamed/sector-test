<template>
  <div id="app">
    <div class="container d-flex justify-content-center">
      <div class="content">
        <entry @add-entry="addEntry"></entry>
        <result :entries="entries"></result>
      </div>
    </div>
  </div>
</template>

<script>
  import Entry from './components/Entry.vue'
  import Result from './components/Result.vue'

  export default {
    name: 'app',
    components: {
      Entry,
      Result
    },
    data () {
      return {
        entries: []
      }
    },
    methods: {
      addEntry (entry) {
        this.entries.push(entry)
      }
    }
  }
</script>

<style lang="scss">
  #app {
    font-family: 'Avenir', Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
    margin-top: 60px;
  }
  .content {
    width: 580px;
  }
</style>
