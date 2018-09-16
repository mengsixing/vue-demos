<template>
  <div id="app">
    <h2>vue key测试(打开控制台查看效果)。</h2>
    <div>
      <div>原始数组:
        <div v-once> {{array}}</div>
      </div>
      <div>改变后数组:
        <div v-once> {{arrayChange}}</div>
      </div>
    </div>
    <h3>使用index作为v-bind:key</h3>
    <div v-for="(item,index) in array" v-bind:key="index">
      <Text2 :msg="item.name" />
    </div>
    <button @click="changeArray">点击改变数组</button>
    <hr />

    <h3>使用item.id作为v-bind:key</h3>
    <div v-for="item2 in array2" :key="item2.id">
      <Text2 :msg="item2.name" />
    </div>
    <button @click="changeArray2">点击改变数组</button>
    <hr/> 在 v-for 中使用 index 时，当数组中间插入一项时，会导致该项之后的其他项都重新渲染，不能起到性能优化效果。
  </div>
</template>

<script>

/*eslint no-console: ["off"] */
import Text2 from './components/Text.vue';

export default {
  name: 'app',
  components: {
    Text2
  },
  data(){
    return {
      array:[{
        id:1,
        name:'name1'
      },{
        id:2,
        name:'name2'
      },{
        id:3,
        name:'name3'
      },{
        id:4,
        name:'name4'
      },{
        id:5,
        name:'name5'
      }],
      array2:[{
        id:'a1',
        name:'name1'
      },{
        id:'a2',
        name:'name2'
      },{
        id:'a3',
        name:'name3'
      },{
        id:'a4',
        name:'name4'
      },{
        id:'a5',
        name:'name5'
      }],
      arrayChange:[{
        id:1,
        name:'name1'
      },{
        id:2,
        name:'name2'
      },{
        id:3,
        name:'name3'
      },
      {
        id:33,
        name:'name33'
      },{
        id:4,
        name:'name4'
      },{
        id:5,
        name:'name5'
      }]
    }
  },
  mounted(){
    console.log('--------初始化完毕--------');
  },
  updated(){
    console.log('--------更新完毕--------');
  },
  methods:{
    changeArray(){
      this.array = this.arrayChange;
    },
    changeArray2(){
      this.array2 = [{
        id:'a1',
        name:'name1'
      },{
        id:'a2',
        name:'name2'
      },{
        id:'a3',
        name:'name3'
      },
      {
        id:'a33',
        name:'name33'
      },{
        id:'a4',
        name:'name4'
      },{
        id:'a5',
        name:'name5'
      }]
    }
  },
}
</script>
