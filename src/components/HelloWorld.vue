<template>
  <div>

    <ul>
      <li v-for="(mostrar, index) in lista" :key="index">

        <strong> Nombre:</strong>{{ mostrar.name.title }} {{ mostrar.name.first }} {{ mostrar.name.last }},
        <strong>genero:</strong> {{ mostrar.gender }}, <strong>pais:</strong> {{ mostrar.location.country }}

        <img :src="mostrar.picture.medium" />
        <div v-if="mostrar.dob.age >= 18 && mostrar.dob.age < 50">
          <strong>Rango de edad: </strong> adulto
        </div>
        <div v-else-if="mostrar.dob.age <= 17">
          <strong>Rango de edad: </strong> niño
        </div>
        <div v-else-if="mostrar.dob.age >= 50">
          <strong>Rango de edad: </strong> abuelo
        </div>


        <button @click="say('email: '+mostrar.email+ ' \n'+'ciudad: '+mostrar.location.city+ ' ' )">Mostrar mas información</button>





        <br><br> <br><br>
      </li>
    </ul>
  </div>
</template>

<script>
import datos from "./users.json";
export default {
  name: "AppVue",
  data() {


    return {
      lista: [],
      textoj: String,
      event: "click"
    };
  },
  mounted() {
    this.lista = datos;
    this.textoj = JSON.stringify(datos.data);
    // console.log(this.textoj);
    datos.forEach(item => { console.log(item.name); });
  },
  methods: {
    say(message) {
      alert(message)
    }
  }



};




</script>






<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
