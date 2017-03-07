<template>
  <div id="app">
    <!-- <img src="./assets/logo.png"> -->
    <!-- <router-view></router-view> -->
    <h1 v-html="title"></h1>
    <input v-model="newItem" v-on:keyup.enter="addNew">
    <ul>
      <li v-for="item in items" v-bind:class="{finished:item.isFinished}" v-on:click="toggleFinished(item)">
        {{item.label}}
      </li>
    </ul>
    <p>{{childWord}}</p>
    <Header-a thisisyoufaher="you die" v-on:child-tell-me-something='ListenTowMyBoy'></Header-a>
  </div>
</template>

<script>
import Store from './store.js'
import HeaderA from './components/header'
export default {
  data () {
    return {
      title: '<span>?</span>Welcome to Your Vue.js App',
      items: Store.fetch(),
      newItem: '',
      childWord: ''
    }
  },
  components: { HeaderA },
  watch: {
    items: {
      handler: function (items) {
        Store.save(items)
      },
      deep: true
    }
  },
  methods: {
    toggleFinished: function (item) {
      item.isFinished = !item.isFinished
    },
    addNew: function () {
      this.items.push({
        label: this.newItem,
        isFinished: false
      })
      this.newItem = ''
      Store.save()
    },
    ListenTowMyBoy: function (msg) {
      this.childWord = msg
    }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
ul{
  width:300px;
  height:150px;
  margin: 0 auto;
}
.finished{
  text-decoration: underline;
}
</style>
