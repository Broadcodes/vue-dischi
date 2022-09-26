<template>
  <div id="app">
    <header>
      <headerComponent />
    </header>
    <main>

    </main>
  </div>
</template>

<script>
import axios from 'axios';

import headerComponent from './components/headerComponent.vue';

export default {
  name: "App",
  data(){
    return {
      itemDisk: [],
    }
  },
  components: {
    headerComponent
},
  created(){
    axios.get('https://flynn.boolean.careers/exercises/api/array/music')
    .then(({data, status}) => {
      if(status === 200){
        this.itemDisk.push(data.response);
        console.log(data.response);
      }
    })
  }
};
</script>

<style lang="scss">
#app {
  font-family: sans-serif;

  * {
    box-sizing: border-box;
    margin: 0px;
    padding: 0px;
  }
}
</style>
