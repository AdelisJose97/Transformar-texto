<template>
  <div id="app">
    <div id="nav">
      <b-navbar variant="info" type="dark" toggleable="lg">
        <b-navbar-brand href="#">Transfor Text</b-navbar-brand>
        
        <b-navbar-toggle target="nav-collapse" ></b-navbar-toggle>

        <b-collapse id="nav-collapse" is-nav >
        <b-navbar-nav>
          <b-nav-item href="#">Opcion 1</b-nav-item>
          <b-nav-item href="#" >Opcion 2</b-nav-item>
        </b-navbar-nav>
        </b-collapse>

      </b-navbar> 
      
          
      <div class="container text-center mt-5" >
        <h1>Convierte tu texto a la opcion que prefieras!</h1>
       </div>

       <div class="container text-center mt-4">
         <b-button variant="outline-info" class="mx-2" @click="convertirMay">Mayusculas</b-button>
         <b-button variant="outline-info" class="mx-2" @click="convertirMin">Minusculas</b-button>
         <b-button variant="outline-info" class="mx-2" @click="convertirCapitalize">Capitalizado</b-button>
         <b-button variant="outline-info" class="mx-2" @click="convertirCapitalizeParrafo">Capitalizar luego de un punto.</b-button>
         <b-button variant="outline-info" class="mx-2">Alternar</b-button>
         <b-button variant="outline-info" class="mx-2">Invertir</b-button>

       </div>
       <div class="container text-center mt-5">
         <b-form-textarea
          id="textarea-rows"
          placeholder="Ingresa tu parrafo aqui!"
          rows="10"
          v-model="parrafo"
          >
          </b-form-textarea>

       </div>

       <p>{{parrafo}}</p>
      





      <!-- <router-link to="/">Home</router-link> |
      <router-link to="/about">About</router-link> -->
    </div>
   <!--  <router-view/> -->
  </div>
</template>

<script>
export default {
  data(){
    return{
      parrafo: ''
    }
  },
  methods:{
    convertirMin(){
      this.parrafo = this.parrafo.toLowerCase();
      
    },
    convertirMay(){
      this.parrafo = this.parrafo.toUpperCase();
      
    },
  
    convertirCapitalize(){
      String.prototype.capitalize = function() {
        return this.toLowerCase().replace(/(^|\s)([a-z])/g, function(m, p1, p2) { return p1 + p2.toUpperCase(); });
};
    
     this.parrafo = this.parrafo.capitalize();
    },
    convertirCapitalizeParrafo(){
      String.prototype.trim = function () {
        return this.replace(/^\s+/, '').replace(/\s+$/, '');
      };
    
    String.prototype.capitalizeParagraph = function() {
        var res = "";
        var paragraphs = this.split(".");
        for(var i = 0; i < paragraphs.length ; i++) {
            var temp = paragraphs[i].trim();
            res += ". " + temp.charAt(0).toUpperCase() + temp.slice(1).toLowerCase();
        }
        return res.slice(1);
    };
    this.parrafo = this.parrafo.capitalizeParagraph();
        }
  }
}
</script>


