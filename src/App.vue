<template>
  <div id="app">
    <div class="shuffle">
      <button @click="shuffle()">Shuffle </button>
    </div>
    <div class="componentList" >
        <div class="componentBox" :index="index"  :key="item"  v-for="(item,index) in this.components">
            <component :is="item" class="tab"></component>
        </div>
    </div>
  </div>
</template>

<script>
import component1 from '@/components/component1'
import component2 from "@/components/component2";
import component3 from "@/components/component3";
import component4 from "@/components/component4";
import component5 from "@/components/component5";
import component6 from "@/components/component6";
import Vue from "vue";

export default {
  name: 'App',
  components: {
    component1,
    component2,
    component3,
    component4,
    component5,
    component6
  },
  data:()=>{
    return{
      test:1,
      components:["component1","component2","component3","component4","component5","component6"]
    }
  },
  methods:{

    shuffle() {
      for (let i =   this.components.length - 1; i > 0; i--) {
        const j = Math.floor(Math.random() * (i + 1));
        const temp =   this.components[i];
        Vue.set(  this.components, i,   this.components[j]);
        Vue.set(  this.components, j, temp);
      }
    }
  }
}
</script>

<style lang="css">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  width: 100%;
  height: 100%;
  display: flex;
  flex-direction: row;
  justify-content: space-evenly;
  align-items: center;
  flex-wrap: wrap;

}

.componentList{
  display: flex;
  flex-wrap: wrap;
  text-align: center;
  align-items: center;
  justify-content: center;
}
.componentBox{
  border: 1px solid white;
  min-height: 200px;
  width: 300px;
  display: flex;
  align-items: center;
  background: #afafaf;
  color: #3c4dc7;
  box-shadow: 1px 1px 20px 5px #e3e0e9;
  justify-content: center;
  font-size: 50px;
}
</style>
