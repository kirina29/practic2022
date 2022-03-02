<template>
  
    <div class="weather">
      <div class="city">
        <p class="weather__city">Магнитогорск</p>
      </div>
      <div class="date">
        <p class="weather__date"></p>
      </div>
      <div class="img">
        <p class="weather__img">
          <img class="weather_img" alt="weather" src="../assets/weather.png">
        </p>
      </div>
      <div class="time">
        <p class="weather__time"></p>
      </div>
      <div class="degree">
        <p class="weather__degree"></p>
        <p class="weather__feel"></p>

      </div>
      <div class="data">
        <p class="weather__humidity"></p>
        <p class="weather__wind"></p>
        <p class="weather__desc"></p>

      </div>
    </div>
    
</template>

<script>
export default {
  name: 'WidgetWeather'
}
fetch('https://api.openweathermap.org/data/2.5/onecall?lat=53.4186&lon=59.0472&appid=b7ac0ad14c496d9957c7d83f9ffd0ded&units=metric&lang=ru').then(function (resp) {return resp.json() }).then(function (data) {

let date=new Date();
let day=String(date.getDate());
let hour=String(date.getHours());
let minute=String(date.getMinutes());
let month=String(+date.getMonth()+1);

document.querySelector('.weather__degree').textContent = Math.round(data.current.temp) + 	' °';
document.querySelector('.weather__date').textContent = day.padStart(2,'0')+'.'+month.padStart(2,'0') +'.'+date.getFullYear();
document.querySelector('.weather__time').textContent = hour.padStart(2,'0')+':'+minute.padStart(2,'0');
document.querySelector('.weather__wind').textContent = 'Ветер: '+data.current.wind_speed + 	' м/с';
document.querySelector('.weather__humidity').textContent = 'Влажность: '+data.current.humidity + 	' %';
document.querySelector('.weather__feel').textContent =  'Ощущается: '+Math.round(data.current.feels_like) + 	' °';
document.querySelector('.weather__desc').textContent = data.current.weather[0]['description'];
})

</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

.weather{
  display:grid;
  width:30%;
  min-width:250px;
  height:20%;
  background: url("../assets/nebo.jpg");
  background-size:cover;
  grid-template-areas:  "city date"
                        ". time"
                        "degree .";
  margin:0 auto;
  border-radius:20px;
  color:white;
  font-family: Century Gothic;

}
.weather .city{
  grid-area:city;
  justify-content:start;
}
.weather__city{
  text-align:start;
  padding-left:10px;
}
.weather .date{
  grid-area:date;
}
.weather__date{
        text-align:end;
          padding-right:10px;


}
.weather_img{
  width:100px;
  filter:brightness(70%);
}
.weather .time{
  grid-area:time;
  align-self:center;
}
.weather__time{
  font-size:50px;
    margin:0;
      text-align:center;


}
.weather__degree{
  font-size:45px;
    margin:0;
      text-align:center;


}
.weather__img{
  text-align:center;
margin:0;
}
.weather .degree{
  grid-area:degree;
}
.weather__feel{
margin:0;

}
.weather .data{
  text-align:start;
}
.weather__humidity{
margin:0;

}
.weather__wind{
  margin:0;

}
</style>
