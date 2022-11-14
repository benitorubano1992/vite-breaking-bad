<script>
import { store } from "./store";
import Appheader from './components/Appheader.vue';
import AppCharList from './components/AppCharList.vue';
import AppChoiceSerie from "./components/AppChoiceSerie.vue";
export default {
  components: {
    Appheader,
    AppCharList,
    AppChoiceSerie
  },
  data() {
    return {
      store,
      hasDataBeenFetch: null
    }
  },
  created: function () {
    this.getCharacterList();
  },
  methods: {
    printName: function () {
      console.log(store.serieName);
    },
    getCharacterList() {
      this.hasDataBeenFetch = false;
      let stringUrl = "https://www.breakingbadapi.com/api/characters";
      this.store.serieName ? stringUrl += `?category=${this.store.serieName}` : stringUrl;

      fetch(stringUrl)
        .then(resp => resp.json())
        .then(data => this.store.characters = data)
        .finally(() => this.hasDataBeenFetch = true)
    }
  }


}

</script>
<template>
  <div class="wrapper">
    <div class="container d-flex flex-column ">
      <Appheader />
      <AppChoiceSerie @selectSerie="getCharacterList" />
      <main>
        <div class="loader d-flex flex-column align-items-center justify-content-center" v-if="!hasDataBeenFetch">
          <div class="rotate">

          </div>
          <p>You request is loading</p>
        </div>

        <AppCharList v-else />
      </main>

    </div>

  </div>
</template>
<style lang="scss">
@use "./styles/general.scss" as *;
@use"./styles/partials/variables" as *;

.wrapper {
  width: 100%;
  height: 90vh;
  position: absolute;
  top: 50%;
  transform: translateY(-50%);
  left: 0;
  background-color: $bg-app;

  .container {
    height: 100%;
  }

  main {
    margin-top: 50px;
    min-height: 400px;
    position: relative;
    overflow-y: auto;

    .loader {
      height: 400px;

      text-transform: uppercase;


      p {
        position: absolute;
        top: 20px;
        left: 0;
        width: 100%;
        color: white;
        text-transform: uppercase;
        font-weight: bold;
        font-size: 2rem;
        text-align: center;
      }

      .rotate {
        height: 100px;
        width: 200px;
        background-color: red;
        margin-bottom: 30px;
        animation: mymove 2s infinite linear;



      }

    }

    @keyframes mymove {
      50% {
        transform: rotate(180deg);
      }
    }

  }

}
</style>