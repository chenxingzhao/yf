<template>
  <div id="app">
    <source-com :source="source" :num="num" @jians="jian" @adds="add">
    </source-com>
    <div>
      男士：{{num.man}} 女士：{{num.woman}} 儿童：{{num.child}}
    </div>
    <div>
      {{zojie}}
    </div>
  </div>
</template>

<script>

import SourceCom from "./components/SourceCom";
export default {
  name: 'App',
  components: {
    SourceCom
  },
  data(){
    return {
      source:{
        man:'N034',
        woman:'V034',
        child:'E034',
        manPrice:'15',
        womanPrice:'15',
        childPrice:'7'
      },
      num:{
        man:1,
        woman:2,
        child:3
      },
      man:['N304'],
      woman:['V304','V305'],
      child:['E304','E305','E306']
    }
  },
  methods:{
    jian(value){
      if(this.num[value]==1){
        alert('最低数量是1')
        return
      }
      this.num[value]--;
      this[value].pop();
    },
    add(value){
      this.num[value]++;
      let pushs=Number(this[value][0].slice(1));
      this[value].push(this[value][0][0]+(pushs+this.num[value]));
    }
  },
  mounted() {

  },
  computed:{
    zojie(){
      return this.man.join('、')+'、'+this.woman.join('、')+'、'+this.child.join('、');
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
