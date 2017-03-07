<template>
	<div id="hader">
		<h1>{{msg}}</h1>
		<h1>{{thisisyoufaher}}</h1>
		<button v-on:click="onClickMe">Click</button>
	</div>
</template>
<script>
export default {
  data () {
    return {
      msg: '哇哈哈'
    }
  },
  props: ['thisisyoufaher'],
  methods: {
    onClickMe: function () {
      this.$emit('child-tell-me-something', this.msg)
    }
  }
}

</script>
<style scoped>
h1, h2 {
  font-weight: normal;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: inline-block;
  margin: 0 10px;
}

a {
  color: #42b983;
}
</style>
