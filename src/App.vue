<template>
  <div id="app">
    <source-com :source="source" :num="num" @jians="jian" @adds="add">
    </source-com>
    <div>
      男士：{{num.man}} 女士：{{num.woman}} 儿童：{{num.child}}
    </div>
    <div>
      {{zojieArray.join('、')}}
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
      zojieArray:[]
    }
  },
  methods:{
    jian(value){
      if(this.num[value]==0){
        alert('最低数量是0')
        return
      }
      this.num[value]--;
      this.zojie();

    },
    add(value){
      this.num[value]++;
      this.zojie();
    },
    zojie(){
       let shu=Number(this.source.man.slice(1));
       this.zojieArray=[];
     for(let item in this.num){
        for(let i=0;i<this.num[item];i++){
          let shuju=shu<100 ? '0'+shu++ : shu++; 
          this.zojieArray.push(this.source[item][0]+shuju);
        }
     }
      
    }
  },
  mounted() {
    this.zojie();
  },
  computed:{
    // zojie(){
    //   return this.man.join('、')+'、'+this.woman.join('、')+'、'+this.child.join('、');
    // }
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
