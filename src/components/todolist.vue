<template>
    <div>
        <input type="text" v-model="inputxt" @keyup.enter="add"/>
        <button @click="add">添加</button>
        <button @click="delect">删除</button>
        <ul>
            <li v-for="(vlist,index) in list" :key="index" @click="toggle(index)" :class="{'undeline': vlist.done }">{{ vlist.text }}</li>
        </ul>
        <p>{{remain}}/{{list.length}}</p>
    </div>
</template>

<script>
export default {
  name: 'todolist',
  data () {
    return {
      inputxt: '',
      list: [
        {text: '吃饭', done: false},
        {text: '睡觉', done: false}
      ]
    }
  },
  computed: {
    remain () {
      return this.list.filter(v => !v.done).length
    }
  },
  methods: {
    add () {
      this.list.push({text: this.inputxt, done: false})
      console.log(this.list)
      this.inputxt = ''
    },
    toggle (index) {
      this.list[index].done = !this.list[index].done
    },
    delect () {
      this.list = this.list.filter(v => !v.done)
    }
  }
}
</script>

<style>
.undeline{
    text-decoration: line-through;
    color:red;
}
</style>

