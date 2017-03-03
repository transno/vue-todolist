<template>
  <div class="hello">
    <input type="text" v-model="text" placeholder="输入回车添加Todolist" @keyup.enter="addList">
    <ul>
      <li v-for="items in list"><span>{{items.msg}}</span><i @click="removeList(items)">×</i></li>
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
      },
      removeList (i) {
        this.list.splice(i, 1);
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
    margin: 10px auto;
    position: relative;
    width: 200px;
  }
  i {
    position: absolute;
    display: block;
    top: 0;
    right: 0;
    cursor: pointer;
  }
  a {
    color: #42B983;
  }
</style>
