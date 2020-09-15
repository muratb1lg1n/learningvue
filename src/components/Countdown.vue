<template>
  <div v-if="yuk">
    <h1>{{ msg }}</h1>
    <div id="app">
      <div class="container">
        <span id="gunler">{{gostergun}}</span>
        <p>Gun</p>  
      </div>
      <div class="container">
        <span id="ciftnokta">:</span>
      </div>
      <div class="container">
        <span id="saatler">{{gostersaat}}</span>
        <p>Saat</p>
      </div>
      <div class="container">
        <span id="ciftnokta">:</span>
      </div>
      <div class="container">
        <span id="dakikalar">{{gosterdak}}</span>
        <p>Dakika</p>  
      </div>
      <div class="container">
        <span id="ciftnokta">:</span>
      </div>
      <div class="container">
        <span id="saniyeler">{{gostersan}}</span>
        <p>Saniye</p>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Countdown',
  data: () => ({
    gostergun: 0,
    gostersaat: 0,
    gosterdak: 0,
    gostersan: 0,
    yuk: false,
  }),
  computed: {
    _san: () => 1000,
    _dak(){
      return this._san * 60;
    },
    _saat(){
      return this._dak * 60;
    },
    _gun(){
      return this._saat * 24;
    },

  },
  methods: {
    kalansure(){
      const zamanla = setInterval(()=>{
        const birthday = new Date(2020 ,10 ,7 ,17 ,45 ,0);
        const simdi = new Date();
        const fark = birthday - simdi;
        
        if (fark < 0){
          clearInterval(zamanla);
          return ;
        }

        const gun = Math.floor(fark / this._gun);
        const saat = Math.floor((fark % this._gun) / this._saat);
        const dak = Math.floor((fark % this._saat) / this._dak);
        const san = Math.floor((fark % this._dak) / this._san);

        this.gostergun = gun;
        this.gostersaat = saat < 10 ? "0" + saat : saat;
        this.gosterdak = dak < 10 ? "0" + dak : dak;
        this.gostersan = san < 10 ? "0" + san : san;
        
        this.yuk = true;
      } ,1000)
    },
  },
  mounted(){
    this.kalansure();
  },
  props: {
    msg: String
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
body{
  background-image: url("https://i.pinimg.com/originals/e2/3d/9c/e23d9cb44dd465c75ac4455c81a07a50.jpg");
  
  text-align: center;

  display: flex;
  flex-direction: column;

}

#app{
  display: flex;
  justify-content: center;
  padding: 10px;
  position: relative;
  margin-top:  5%;
  
}

p {
  font-family: "Lucida Console", Monaco, monospace;
  padding: 10px;
  font-size: 45px;
  
}

span {
  font-family: "Lucida Console", Monaco, monospace;
  font-size: 65px;
}
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
