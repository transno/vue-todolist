<template>
  <div class="hello">
    <input type="text" v-model="text" placeholder="输入回车添加Todolist" @keyup.enter="addList">
    <ul>
      <li v-for="items in list">{{items.msg}}</li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'hello',
  data () {
    return {
      text: '',
      list: []
    }
  },
  methods: {
    addList () {
        this.list.push({msg: this.text});
        this.text = '';
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1, h2 {
  font-weight: normal;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: block;
  margin: 10px;
}

a {
  color: #42b983;
}
</style>
