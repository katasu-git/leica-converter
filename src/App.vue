<template>
  <div id="app">
    <div id="header-text">Leica M10 : ¥{{digitSeparator(leicaYen)}}</div>
    <div id="center-contents">
      <img id="leica-image" :style="{opacity: imageOpacity()}" alt="leica" src="./assets/leica.png">
      <div class="mt-20">{{convertYenToLeica(128900)}} <span class="leicaRed">L</span>eica!!</div>

      <div id="form">
        <div id="unit">yen</div>
        <input type="number" v-model="userEnterYen" placeholder="ENTER JPY!!">
      </div>
    </div>
    <div id="cr">powered by maguro no kuni</div>
  </div>
</template>

<script>
//import HelloWorld from './components/HelloWorld.vue'

export default {
  name: 'App',
  data() {
    return {
      leicaYen: 919600,
      userEnterYen: 100000,
      op: '50%'
    }
  },
  methods: {
    digitSeparator(num) {
      return num.toLocaleString();
    },
    convertYenToLeica() {
      return (this.userEnterYen / this.leicaYen).toFixed(6)
    },
    imageOpacity() {
      return this.convertYenToLeica() * 100 + '%'
    }
  }
}
</script>

<style>
html, body, #app {
  width: 100%;
  height: 100%;
  font-family: Avenir, Helvetica, Arial, sans-serif;
  font-weight: bold;
  font-size: 18px;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  background: black;
  color: white;
  margin: 0;
  padding: 0;
}

#header-text {
  position: absolute;
  top: 10px;
  left: 10px;
  font-size: 12px;
}

#center-contents {
  padding: 10px;
  font-size: 36px;
  position: absolute;
  top: 5%;
  right: 0;
  bottom: 0;
  left: 0;
  margin: auto;
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
}

#leica-image {
  transition-property: all;
  transition-duration: 300ms;
  transition-delay: 0s;
  transition-timing-function: ease;
}

#form {
  margin-top: 80px;
  position: relative;
}

input {
  height: 60px;
  width: 100%;
  border: none;
  border-radius: 3px;
  text-align: center;
  font-size: 36px;
  font-weight: bold;
}

#unit {
  position: absolute;
  bottom: 5px;
  right: 5px;

  font-size: 24px;
  color: black;
}

.mt-20 {
  margin-top: -20px;
}

#cr {
  position: absolute;
  bottom: 10px;
  right: 10px;
  font-size: 12px;
}

.leicaRed {
  color: #C14441;
}

</style>
