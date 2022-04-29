
<template>
  <div>
     
       
     
    
      <div class="container-new" >
         
          <form @submit="addCliente" class="add-container" >
           
              <input class="inputs" placeholder="Nombre" type="text" v-model="nombre">
              <input placeholder="Apellido" type="text" v-model="apellido">
              <input placeholder="E-mail" type="email" v-model="email">
              <input placeholder="Telefono" type="number" v-model="telefono">
              <input placeholder="Fecha de Nacimiento" type="date" v-model="fecha">
              <input placeholder="Direccion" type="text" v-model="address">
               <input placeholder="Genero" type="text" v-model="tipo">
              <input placeholder="Ciudad" type="text" v-model="origen">
              <div class="actions" >  
                   <input value="Guardar" class="agregar" type="submit">
              </div>
               
             
          </form>

      </div>
  </div>
</template>

<script>
import { v4 as uuidv4 } from 'uuid';
export default {
  name: 'MyClienteAdd',
  data(){
      return {
          nombre: '',
          telefono: '',
          apellido: '',
          email: '',
          fecha: '',
          address: '',
          tipo: '',
          origen: ''
      }
  },
  methods: {
      addCliente(e){
        
          e.preventDefault();
    
          const newCliente = {
              id: uuidv4(),
              nombre: this.nombre,
              telefono: this.telefono,
              completed: false,
              apellido: this.apellido,
              email: this.email,
              fecha: this.fecha,
              direccion: this.direccion,
              tipo: this.tipo,
              origen: this.origen
          };

          this.nombre = '';
          this.telefono = '';
          this.apellido = '';
          this.fecha = '';
          this.tipo = '';
          this.email = '';
          this.genero = '';
          this.origen = '';
          this.address = '';
          
          this.$emit('add-cliente', newCliente)
          console.log(this.id)
      }
  }
  
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

.container-new {
    width: 350px;
    background: rgb(228, 226, 226);
    border-radius: 10px;
    margin-top: 20px;
}
.add-container {
    display: flex;
    justify-content: center;
    align-items: center;
    flex-direction: column;
    width: 100%;
    
}


.agregar::placeholder {
 
 text-align: center;
}

input {
    width: 94%;
    border-radius:10px;
    height: 30px;
    margin: 5px;
    border: none;
    background: white;
    box-sizing: border-box;
    position: relative;
     outline: none;
     padding-left: 15px;
}

input::placeholder {
    margin-left: 20px;
}

.agregar {
    
    background: rgb(32, 221, 105);
    outline: none;
    border: 1px solid black;
    border-radius: 10px;
    margin-bottom: 20px;
    margin-top: 10px;
    height: 20px;
    width: 35%;
    height: 25px;
    color: white;
    font-weight: bold;
    border: none;
    display: flex;
    align-items: center;
    justify-content: center;
}
.agregar:hover{
    background: rgb(16, 160, 71);
}

.cancelar {
    
    background: rgb(221, 32, 32);
    outline: none;
    border: 1px solid black;
    border-radius: 10px;
    margin-bottom: 20px;
    margin-top: 10px;
    height: 20px;
    width: 35%;
    height: 25px;
    color: white;
    font-weight: bold;
    border: none;
}

.actions {
    display: flex;
    flex: row;
    align-items: center;
    justify-content: space-evenly;
    width: 100%;
}

</style>
