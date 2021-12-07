<template>
  <div id="app">
    <h1 class="titulo">Random Gif Cat</h1>

    <form class="form_gif">
      <label for="" class="margin">Titulo: </label>
      <input type="text" v-model="tituloGif" class="margin"><br>
      <!--seleccion del filtro -->
      <label for="" class="margin">Filtro: </label>
      <select @change.prevent="changeFilter " class="margin">
        <option v-for="filtro in filtroOpc" :key="filtro.value" :value="filtro.value">{{filtro.filter}}</option>
      </select><br>

      <!--seleccion del color -->
      <label for="" class="margin">Color: </label>
      <select @change.prevent="changeColor" class="margin">
        <option v-for="color in colorOpc" :key="color.value" :value="color.value">{{color.color}}</option>
      </select><br>

      <!--seleccion del tamaño-->
      <label for="" class="margin">Tamaño: </label>
      <input type="text" v-model="size" class="margin">
    </form>
    

    <button @click.prevent="fetchCats" class="margin">Obtener mi gatito</button><br>

    <img v-if="image != `  `" :src="image" alt="gatito" class="margin">
  </div>
</template>

<script>


export default {
  name: 'App',
  data(){
    return{
      tituloGif: " ",
      image: `  `,
      size: " ",
      filter: "blur",
      color: "green",
      filtroOpc:[
        {
          filter:"Blur",
          value:"blur",
        },
        {
          filter:"Mono",
          value: "mono",
        },
        {
          filter:"Sepia",
          value: "sepia",
        },
        {
          filter:"Negative",
          value: "negative",
        },
        {
          filter:"Paint",
          value: "paint",
        },
        {
          filter:"Pixel",
          value: "pixel",
        },

      ],
      colorOpc:[
        {
          color:"Green",
          value:"green",
        },
        {
          color:"Red",
          value:"red",
        },
        {
          color:"Blue",
          value:"blue",
        },
        {
          color:"Yellow",
          value:"yellow",
        },
        {
          color:"Purple",
          value:"purple",
        },
        {
          color:"Orange",
          value:"orange",
        },
      ]
    }
  },
  computed:{ 
  },
  methods:{
    fetchCats(){
    this.image =`https://cataas.com/cat/gif/says/${this.tituloGif}?filter=${this.filter}&color=${this.color}&size=${this.size}&type=or `
    },
    changeFilter (event){
      //this.filtroOpc = event.target.value
      this.filter = event.target.value
    },

    changeColor (event){
      //this.colorOpc = event.target.value
      this.color = event.target.value
    },


  },

  components: {
    
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  align-content: center;
  color: #2c3e50;
  background-color: #9fc7df;
 
}

.titulo{
  padding-top: 60px ;
  margin-bottom: 50px;
}

.form_gif{
  background-color: #ff637D;
  padding-top: 50px;
  padding-bottom: 50px;
  
}

.margin{
  margin: 20px 0 20px 0;
}


</style>
