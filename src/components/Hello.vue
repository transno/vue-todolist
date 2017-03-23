<template>
  <div class="hello">
    <input type="text" v-model="text" placeholder="输入回车添加Todolist" @keyup.enter="addList">
    <ul>
      <li v-for="(items, index) in list">
        <label><input type="checkbox" v-model="completeList" :value="items.msg"><span>{{items.msg}}</span></label>
        <i @click="removeList(index)" title="删除">×</i>
      </li>
    </ul>
    <span>{{completeList}}</span>
  </div>
</template>

<script>
  export default {
    name: 'hello',
    data () {
      return {
        text: '',
        list: [],
        completeList: []
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
        this.list.splice(i, 1);

        // 以下为改变当前当前列表的显示状态，i传入的是for/in的items
        // 要达到修改对象的某项值，达到arr[index] = value的状态，需要使用
        // this.$set(object, key, value);
        // https://cn.vuejs.org/v2/guide/list.html#注意事项
        //        this.$set(i, 'isDelete', true);
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
    height: 30px;
    line-height: 30px;
    opacity: 0;
  }
  li:hover input[type="checkbox"] ~ span:before, li:hover i {
    opacity: 1;
  }
  a {
    color: #42B983;
  }
  input[type="checkbox"] {
    display: none;
  }
  input[type="checkbox"] ~ span {
    font-size: 16px;
    color: #666;
    position: relative;
    display: block;
    height: 30px;
    line-height: 30px;
  }
  input[type="checkbox"] ~ span:before {
    display: block;
    position: absolute;
    width: 18px;
    height: 18px;
    content: '';
    border-radius: 50%;
    background-color: #FFF;
    border: 1px solid #999;
    top: 50%;
    left: 0;
    transform: translateY(-50%);
    transition: all .2s ease;
    cursor: pointer;
    opacity: 0;
  }
  li input[type="checkbox"]:checked ~ span {
    text-decoration: line-through;
    color: #BBB;
  }
  li input[type="checkbox"]:checked ~ span:before {
    background-color: green;
    border-color: green;
  }
</style>
