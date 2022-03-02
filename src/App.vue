<template>
  <header class="header">
    <img src="./assets/comet.png" width="50" id="train">
  </header>
  <div class="container">
    <div class="text_left item none">
      <p>Всем привет! Я Котляр Ирина, студентка Многопрофильного колледжа. Учусь на 4 курсе по специальности "Разработка веб и мультимедийных приложений".</p>
    </div>
    <div class="text_center item">
      <img class="logo" v-on:click="logo" alt="Vue logo" src="./assets/logo.jpg">
      <h1>Kotlyar Irina</h1>
    </div>
    <div class="text_right item none">
          <p>Я выбрала фронт, потому что он проще и динамичнее, чем бэк. Это работа с интерфейсами, поэтому ты делаешь и практически сразу видишь результат.</p>

    </div>
  </div>
  <WidgetWeather/>
  
</template>

<script>

import WidgetWeather from './components/WidgetWeather.vue'

export default {
  name: 'App',
  components: {
    WidgetWeather
  },
  methods:{
    logo(){
      let text1=document.querySelector('.text_left');
      let text2=document.querySelector('.text_right');
      text1.classList.remove('none');
      text1.classList.add('show');
      setTimeout(() => {  
        text2.classList.remove('none');
        text2.classList.add('show');
      }, 1000);
    }
  }
}
 
</script>

<style>
@keyframes movingBox{
  0%{
    opacity:0;
  }
  25%{
    opacity:0.25;
  }
  50%{
    opacity:0.5;
  }
  75%{
    opacity:0.75;
  }
  100%{
    opacity:1;
  }
}
html{
  margin:0;
  width:100%;
  padding:0;
}
body{
  margin:0;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin:0;
}
h1{
  text-transform: uppercase;
    font-weight: 300;
    letter-spacing: 4px;
    font-size: 3rem;
    width: 554px;
    margin: 16px auto 16px;
}

.header{
  height: 50px;
  background:#1f203a;
  position:relative;
  top:0;
  text-align:left;
}
.header img{
  margin-left:40px;
}
.container{
  display:grid;
  grid-template-areas: "left center right";
  justify-items:center;
  align-items:center;
}
.item p{
font-family:cursive;
}
.none{
 opacity:0;
}
.show{
  animation-name: movingBox;
  animation-duration: .5s;
}
.text_left{
  grid-area:left;
  width:70%;

}
.text_center{
  grid-area:center;

}
.text_right{
  grid-area:right;
  width:70%;

}
.logo{
  margin-top:80px;
  height:400px;
   border-radius: 100%; 
    border: 3px solid #1f203a; 
    box-shadow: 0 0 70px #666; 
    cursor:pointer;
}

</style>
