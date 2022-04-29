
<template>
  <div id="app">
    
    <div id="header">
      <MySearchCliente v-on:query-change="querySearch" />
    </div>

     <h2 class="titulo" >Lista de Contactos</h2>
 
    <div id="main-container">
      <MyClientes v-bind:clientesList="copyClientes" v-on:delete-cliente="deleteCliente"/>
    </div>
   
   <button class="agregar" @click="hide" >Agregar
     <svg xmlns="http://www.w3.org/2000/svg" width="19" height="19" fill="currentColor" class="bi bi-person-plus-fill" viewBox="0 0 16 16">
      <path d="M1 14s-1 0-1-1 1-4 6-4 6 3 6 4-1 1-1 1H1zm5-6a3 3 0 1 0 0-6 3 3 0 0 0 0 6z"/>
      <path fill-rule="evenodd" d="M13.5 5a.5.5 0 0 1 .5.5V7h1.5a.5.5 0 0 1 0 1H14v1.5a.5.5 0 0 1-1 0V8h-1.5a.5.5 0 0 1 0-1H13V5.5a.5.5 0 0 1 .5-.5z"/>
     </svg>
   </button>
   
  <div class="hide" id="hide" >
    <MyClienteAdd v-on:add-cliente="addCliente"/>
  </div>  

 
      
  </div>
</template>

<script>

import MyClientes from './components/MyClientes'
import MyClienteAdd from './components/MyClienteAdd'
import MySearchCliente from './components/MySearchCliente'

export default {
  name: 'App',
  components: {
    MyClientes, MyClienteAdd, MySearchCliente
    
  },
  methods: {
    deleteCliente(id){
       this.copyClientes.splice(id, 1);
          localStorage.setItem('clientes-vue', JSON.stringify(this.copyClientes));
      this.clientes = this.clientes.filter(cliente => cliente.id != id);
      this.copyClientes = [...this.clientes]
        
    },
    addCliente(cliente) {
    
      this.clientes.push(cliente);
      this.copyClientes = [...this.clientes]
       localStorage.setItem('clientes-vue', JSON.stringify(this.copyClientes));        
    },
    hide() {
     let docu = document.getElementById('hide')
        docu.classList.toggle('hide')
      
    },
  

    querySearch(query){
       if (query.trim() ===  '') {
         this.copyClientes = [...this.clientes]
       } else {
         const temp = this.clientes.filter(cliente => {
           return cliente.nombre.includes(query)
         });
         this.copyClientes = [...temp];
       }
    }
  },
  data() {
    return {
      clientes: [{id: 0, nombre: "Luis Cordero", telefono: 3046295775, completed: false,
                  email: "@gmail", apellido: "cordero", tipo: "Hombre", origen:"Monteria-Cordoba"},
      ], 
      copyClientes: []
    }
  },
  created () {
    
    localStorage.setItem('clientes-vue', JSON.stringify(this.clientes));
    
     let theCopyClientes = JSON.parse(localStorage.getItem('clientes-vue'));
    this.clientes = theCopyClientes

    this.copyClientes = [...this.clientes]

    
   
  }
}
</script>



<style>

* {
  font-family: 'Poppins', sans-serif;
}
#app {
   background: white;
   border-radius: 10px;
   display: flex;
   flex-direction: column;
   align-items: center;
   justify-content: center;
}

#header {
  width: 100%;
  height: 40px;
  margin: 0;
  padding: 0;
  display: flex;
  align-items: center;
  justify-content: center;
}

#main-container {
  border-radius: 10% ;
  
}

.titulo {
  
  font-weight: bold;
  color: rgb(0, 102, 255);
  font-size: 1.2em;
  margin-bottom: 3px;
}
.agregar {
    
    background: rgb(0, 102, 255);
    outline: none;
    border: 1px solid black;
    border-radius: 10px;
    margin-bottom: 20px;
    margin-top: 10px;
    height: 30px;
    width: 100px;
    height: 25px;
    color: white;
    font-weight: bold;
    border: none;
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: .9em;
    margin-bottom: 0;
}

.agregar:hover{
   background: rgb(6, 69, 165);
}

.bi-person-plus-fill {
  margin-left: 5px;
}

.hide {
  transition: .5s;
  opacity: 0;
  display: none;
}


</style>
