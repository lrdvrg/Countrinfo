<template>
  <div id="app" class="container">
    <br>
    <select class="custom-select" name="dropdown" id="dropdown" v-model="pais">
      <option v-bind:value="index" v-for="(p, index) in paises" :key="index">{{p.name}}</option>
    </select>
    <hr>
    <h1>{{paises[pais].nativeName}}</h1>  
    <hr>
    <h3>{{paises[pais].capital}}</h3>
    <h6>Capital</h6>
    <hr>
    <h3>{{paises[pais].population}}</h3>
    <h6>Poblacion</h6>
    <hr>
    <h3>{{paises[pais].languages[0].nativeName}}</h3>
    <h6>Lenguaje</h6>
    <hr>
    <section class="text-center">
      <img :src="paises[pais].flag" alt="Bandera" height="200" width="360">
    </section>
    <h6>Bandera</h6>
    <hr>
    <section class="text-center">
      <iframe :src="'https://www.google.com/maps/embed?pb=!1m14!1m12!1m3!1d14921.733104305373!2d'+paises[pais].latlng[1]+'!3d'+paises[pais].latlng[0]+'!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!5e0!3m2!1ses-419!2sdo!4v1565379980828!5m2!1ses-419!2sdo'" width="690" height="350" frameborder="0" style="border:0" allowfullscreen></iframe>
    </section>
  </div>
</template>

<script>
import axios from 'axios'
export default {
  name: 'app',
  data () {
    return {
      paises: null,
      pais: 0,
    }
  },
  mounted(){
    this.getPais();
    
  },
  methods: {
    getPais() {
      axios.get('https://restcountries.eu/rest/v2/all').then(response => {
        this.paises = response.data
        console.log(this.imagen);

      }).catch(e=>console.log(e));
    }
  }
}
</script>

<style>
  h6 {
    color: gray
  }
</style>
