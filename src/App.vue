<template>
  <div id="app">
    <header>
      <headerComponent :albumSearch="itemDisk" @searchDisk="filterDisk"/>
    </header>
    <main>
      <loadingElement v-if="this.loading"/>
      <mainComponent v-else :album="itemDiskToViewBeforeFilter"/>
    </main>
  </div>
</template>

<script>
  // Importo il package axios da npm
import axios from "axios";

import headerComponent from "./components/headerComponent.vue";
import mainComponent from "./components/mainComponent.vue";
import loadingElement from "./components/loadingElement.vue";

export default {
  name: "App",
  data() {
    return {
      // variabile necessaria per gestire la schermata di caricamento in caso di rallentamento della rete
      loading: true,
      // array in cui vengono salvati i dati dell'API
      itemDisk: [],
      itemDiskToViewBeforeFilter: [],
    };
  },
  methods:{
    filterDisk(disk){

      let arr = [];

      this.itemDisk.forEach(item => {
        if(item.title.indexOf(disk) > -1){
          arr.push(item);
        }
      });

      this.itemDiskToViewBeforeFilter = arr;
    }
  },
  components: {
    headerComponent,
    mainComponent,
    loadingElement
},
  created() {
    axios
      .get("https://flynn.boolean.careers/exercises/api/array/music")
      .then(({ data, status }) => {

        // Se vengono trovati i dati possono essere salvati i dati nell'array creato
        if (status === 200) {
          this.loading = false;
          this.itemDisk = data.response;
          this.itemDiskToViewBeforeFilter = data.response;
        }
      })
      // In caso di errore il programma non termina perchè l'errore viene catturato dal catch
      .catch((e) => {
        this.loading = false;
        console.log(e.message);
      });
  },
};
</script>

<style lang="scss">
 * {
    box-sizing: border-box;
    margin: 0px;
    padding: 0px;
  }

#app {
  font-family: sans-serif;
}
</style>
