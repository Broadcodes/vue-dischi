<template>
  <header>
    <i class="logoImg fa-brands fa-spotify"></i>
    <div class="areaFilter" @click="viewAreaSearch">
      <p>Filtra</p>
      <i class="filter fa-solid fa-filter"></i>
    </div>
    <div class="areaSearchBox">
      <select name="filterDisk" id="filterDisk" v-model="disk" @click="selectDisk()" @keyup="selectDisk()">
        <option value="">Filtra per genere</option>
        <option
          v-for="(diskList, index) in filterDiskGenre()"
          :key="index"
          :value="diskList"
        >
          {{ diskList }}
        </option>
      </select>
      <select name="filterAlbum" id="filterAlbum" v-model="album" @click="selectAlbum()" @keyup="selectAlbum()">
        <option value="">Filtra per album</option>
        <option
          v-for="diskListObj in albumSearch"
          :key="diskListObj.title"
          :value="diskListObj.author"
        >
          {{ diskListObj.author }}
        </option>
      </select>
    </div>
  </header>
</template>

<script>
export default {
  name: "headerComponent",
  data() {
    return {
      viewAreaSearchBox: false,
      disk: '',
      album: '',
    };
  },
  props: {
    albumSearch: Array,
  },
  methods: {
    viewAreaSearch() {
      const areaSearchBox = document.querySelector(".areaSearchBox");

      if (this.viewAreaSearchBox) {
        this.viewAreaSearchBox = false;
        areaSearchBox.classList.remove("viewBox");
      } else {
        this.viewAreaSearchBox = true;
        areaSearchBox.classList.add("viewBox");
      }
    },
    selectDisk(){
      this.$emit('searchDisk', this.disk);
    },
    selectAlbum(){
      this.$emit('searchAlbum', this.album);
    },
    filterDiskGenre(){
      const genreDisk = [];

      this.albumSearch.forEach(disk => {
        if(!genreDisk.includes(disk.genre)){
          genreDisk.push(disk.genre);
        }
      });

      return genreDisk;
    }
  },
};
</script>

<style lang="scss" scoped>
header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  background-color: #2e3a46;
  height: 55px;
  padding: 0 10px;
  position: relative;

  .viewBox {
    width: 550px !important;
  }

  .logoImg {
    font-size: 2rem;
    color: #1ed760;
  }

  .areaFilter {
    display: flex;
    cursor: pointer;
    color: #576c83;

    &:hover {
      color: #89a9cc;
    }

    p {
      align-self: center;
      padding-right: 10px;
      font-size: 0.8rem;
    }

    .filter {
      font-size: 1.5rem;
      margin-right: 20px;
    }
  }

  .areaSearchBox {
    position: absolute;
    right: 110px;
    display: flex;
    width: 0px;
    overflow: hidden;
    transition: width 1s;

    select {
      width: 100%;
      height: 30px;
      margin: 0 8px;
      background-color: rgba(255, 255, 255, 0.4);
      border-radius: 5px;
    }
  }
}
</style>