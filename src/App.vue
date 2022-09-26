<template>
  <div id="app">
    <header>
      <headerComponent />
    </header>
    <main>
      <loadingElement v-if="this.loading"/>
      <mainComponent v-else :album="itemDisk"/>
    </main>
  </div>
</template>

<script>
import axios from "axios";

import headerComponent from "./components/headerComponent.vue";
import mainComponent from "./components/mainComponent.vue";
import loadingElement from "./components/loadingElement.vue";

export default {
  name: "App",
  data() {
    return {
      loading: true,
      itemDisk: [],
    };
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
        if (status === 200) {
          this.loading = false;
          this.itemDisk = data.response;
        }
      })
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
