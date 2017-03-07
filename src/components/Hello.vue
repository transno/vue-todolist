<template>
  <div class="hello">
    <input type="text" v-model="text" placeholder="输入回车添加Todolist" @keyup.enter="addList">
    <ul>
      <li v-for="(items, index) in list"><span :class="{delete: items.isDelete}">{{items.msg}}</span><i @click="removeList(items)">×</i></li>
    </ul>
  </div>
</template>

<script>
  export default {
    name: 'hello',
    data () {
      return {
        text: '',
        list: [],
        isDelete: false
      }
    },
    methods: {
      addList () {
        if (this.text == '') return false;
        this.list.push({msg: this.text});
        this.text = '';
      },
      removeList (i) {
        // 以下为删除数组方法，i传入的是for/in的index
        // this.list.splice(i, 1);

        // 以下为改变当前当前列表的显示状态，i传入的是for/in的items
        // 要达到修改对象的某项值，达到arr[index] = value的状态，需要使用
        // this.$set(object, key, value);
        // https://cn.vuejs.org/v2/guide/list.html#注意事项
        this.$set(i, 'isDelete', true);
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
  .delete {
    text-decoration: line-through;
  }
</style>
