<template>
  <div id="app">
    <div class="liste">
      <div class="liste2">
    <ul>
      <li v-for="(result, index) in limitedResults" :key="index">{{ result }}</li>
    </ul>
      </div>
    </div>
    <h1>{{ result }}</h1>
    <img v-if="result === 'Yazı'" :src="yaziPhotoPath" alt="Yazı Fotoğrafı">
    <img v-else-if="result === 'Tura'" :src="turaPhotoPath" alt="Tura Fotoğrafı">
    <button @click="tossCoin">
      Tıkla
    </button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      result: "",
      results: [],
      resultLimit: 5,
      yaziPhotoPath: require('@/assets/yazi.png'),
      turaPhotoPath: require('@/assets/tura.png'),
    };
  },
  computed: {
    limitedResults() {
      return this.results.slice(-this.resultLimit);
    },
  },
  methods: {
    tossCoin() {
      const random = Math.random();
      this.result = random < 0.5 ? "Yazı" : "Tura";
      if (this.results.length === this.resultLimit) {
        this.results.shift();
      }
      
      this.results.push(this.result);
    },
  },
};
</script>

<style>
#app {
  color: #004C99;
  font-size: 30px;
  font-family: Arial, sans-serif;
  text-align: center;
  margin-top: 200px;
}

body{background-color: #2D2E47}

button {
  --bg: #AF40FF;
  --text-color: #fff;
  position: relative;
  width: 150px;
  border: none;
  background: var(--bg);
  color: var(--text-color);
  padding: 1em;
  font-weight: bold;
  text-transform: uppercase;
  transition: 0.2s;
  border-radius: 5px;
  opacity: 0.8;
  letter-spacing: 1px;
  box-shadow: #6E2D9A 0px 7px 2px, #000 0px 8px 5px;
}

button:hover {
  opacity: 1;
}

button:active {
  top: 4px;
  box-shadow: #572579 0px 3px 2px,#000 0px 3px 5px;
}
.liste {
        color:#004C99;
        position:absolute;
        top: 54%;
        left: 43.23%;
        font-family: Arial Black;
        font-size: 30px;
        width: 195px;
        height: 270px;
        border-radius: 20px;
        padding: 5px;
        box-shadow: rgba(151, 65, 252, 0.2) 0 15px 30px -5px;
        background-image: linear-gradient(144deg,#AF40FF, #5B42F3 50%,#00DDEB);
        }
.liste2 {position:absolute;
  background: rgb(5, 6, 45);
  border-radius: 17px;
  width: 95%;
  height: 95%;
}        
img {
  position:absolute;
  top: 1%;
  left: 45%;
  width: 10%;
}
</style>
