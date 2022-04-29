

<template>
  <div  v-bind:class="{completed: cliente.completed}">
      
      <div  class="cliente-body">
          
            <div class="contacto">
                <p>{{cliente.nombre}}</p>
                <p>(+57) {{cliente.telefono}}</p>
            </div>

        
          
          <div class="cliente-actions">
             
               <button  @click="$emit('edit-cliente', cliente.id)" >
                    <svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" fill="currentColor" class="bi bi-pencil-fill" viewBox="0 0 16 16">
                    <path d="M12.854.146a.5.5 0 0 0-.707 0L10.5 1.793 14.207 5.5l1.647-1.646a.5.5 0 0 0 0-.708l-3-3zm.646 6.061L9.793 2.5 3.293 9H3.5a.5.5 0 0 1 .5.5v.5h.5a.5.5 0 0 1 .5.5v.5h.5a.5.5 0 0 1 .5.5v.5h.5a.5.5 0 0 1 .5.5v.207l6.5-6.5zm-7.468 7.468A.5.5 0 0 1 6 13.5V13h-.5a.5.5 0 0 1-.5-.5V12h-.5a.5.5 0 0 1-.5-.5V11h-.5a.5.5 0 0 1-.5-.5V10h-.5a.499.499 0 0 1-.175-.032l-.179.178a.5.5 0 0 0-.11.168l-2 5a.5.5 0 0 0 .65.65l5-2a.5.5 0 0 0 .168-.11l.178-.178z"/>
                    </svg>
                </button>
                 
                 <button @click="showModal = true">
                    <svg xmlns="http://www.w3.org/2000/svg" width="18" height="18" fill="currentColor" class="bi bi-three-dots" viewBox="0 0 16 16">
                    <path d="M3 9.5a1.5 1.5 0 1 1 0-3 1.5 1.5 0 0 1 0 3zm5 0a1.5 1.5 0 1 1 0-3 1.5 1.5 0 0 1 0 3zm5 0a1.5 1.5 0 1 1 0-3 1.5 1.5 0 0 1 0 3z"/>
                    </svg>
                </button>

                <button @click="$emit('delete-cliente', cliente.id)" >
                    <svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" fill="currentColor" class="bi bi-trash3-fill" viewBox="0 0 16 16">
                    <path d="M11 1.5v1h3.5a.5.5 0 0 1 0 1h-.538l-.853 10.66A2 2 0 0 1 11.115 16h-6.23a2 2 0 0 1-1.994-1.84L2.038 3.5H1.5a.5.5 0 0 1 0-1H5v-1A1.5 1.5 0 0 1 6.5 0h3A1.5 1.5 0 0 1 11 1.5Zm-5 0v1h4v-1a.5.5 0 0 0-.5-.5h-3a.5.5 0 0 0-.5.5ZM4.5 5.029l.5 8.5a.5.5 0 1 0 .998-.06l-.5-8.5a.5.5 0 1 0-.998.06Zm6.53-.528a.5.5 0 0 0-.528.47l-.5 8.5a.5.5 0 0 0 .998.058l.5-8.5a.5.5 0 0 0-.47-.528ZM8 4.5a.5.5 0 0 0-.5.5v8.5a.5.5 0 0 0 1 0V5a.5.5 0 0 0-.5-.5Z"/>
                    </svg>
                </button> 
                <div class="select" >
                    <input class="checkbox" type="checkbox" 
                    v-bind:checked="cliente.completed ? 'checked' : ''"
                    v-on:change="checkCliente">
                </div>

          </div>
      
      </div>
        <transition name="fade" >
             <div class="modal-overlay" v-if="showModal">
                 <h3>Datos del contacto</h3>
                 <div class="datos" >
                    <span>{{cliente.nombre}} {{cliente.apellido}}</span>
                    <span>(+57){{cliente.telefono}}</span>
                    <span>{{cliente.email}}</span>
                    <span>{{cliente.tipo}}</span>
                    <span>{{cliente.origen}}</span>
                    <span>{{cliente.fecha}}</span>
                 </div>
            
                <button class="cerrar-modal"  @click="showModal = false">cerrar</button>
             </div>
        </transition>
     
  </div>
</template>
  
<script>
/* eslint-disable */
export default {
  name: 'MyClientesItem',
  data(){
      return {
             showModal: false
      }
     
  },
  props: ['cliente'],
  methods: {
      checkCliente(){
          this.cliente.completed = !this.cliente.completed; //eslint-disable-next-line
          
           
      }
  }
}
 
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>


.cliente-body {
     width: 80%;
     height: 50px;
     display: flex;
     justify-content: space-between;
     align-items: center;
     *border: 1px solid black;
      width: 300px;
      position: relative;

}

.cliente-body::before {
    position: absolute;
    content: "";
    width: 100%;
    height: 3px;
    background: #fff;
    bottom: 0;
}

.contacto {

    *border: 1px solid black;
    width: 70%;
    height: 50px;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;    
}


p {
    
    *border: 1px solid black;
    margin: 0 auto;
    width: 90%;
    height: 35%;
    
}

p:nth-child(1) {
    color: rgb(32, 32, 32);
    font-size: 1em;
    font-weight: 700;
     margin-top: 3px;
     text-transform: capitalize;
}
p:nth-child(2) {
    color: rgb(0, 102, 255);
    font-size: .8em;
    font-weight: 500;
    margin-top: 8px;
    margin-bottom: 8px;
}


.cliente {
    display: flex;
    justify-content: center;
    align-items: center;
    background: rgba(232, 238, 234, 0.918);
    width: 30%;
   
    width: 300px;
    *border-radius: 5px;
    border: none;
    
}

.completed {
    background: rgb(224, 223, 223);
    text-decoration: line-through;
   
}

button {
    border: none;
    background: transparent;
    cursor: pointer;
}

svg{
    color: rgb(0, 102, 255);
    transition: .4s;
}

svg:hover{
  color: rgb(8, 47, 105);
  transform: scale(1.2);
}

.cliente-actions {
    display: flex;
}

.checkbox {
  height: 20px;
}

.fade {
    display: flex;
    align-items: center;
    justify-content: center;
    transition: .8s;
}

.modal-overlay {
    position: absolute;
   
    width: 300px;
    height: 250px;
    z-index: 100;
    border-radius: 10px;
     background: rgba(232, 238, 234, 1);
    box-shadow: 2px 2px 2px 1px rgba(0, 0, 0, 0.2);
    
    display: flex;
    align-items: center;
    justify-content: space-evenly;
    flex-direction: column;
}

.cerrar-modal {
    border: none;
    background: rgb(0, 102, 255);
    cursor: pointer;
    border-radius:10px;
    display: block;
    color: #fff;
    font-weight: bold;
    width: 100px;
    letter-spacing: 2px;
}
.datos {
    display: flex;
    flex-direction: column;
    align-items: flex-start;
    margin-left: 3px;
    height: 70%;
    margin-top: 20px;
    width: 90%;
}
h3 {
    margin: 0;
    padding: 0;
    height: 10px;
    color: rgb(0, 102, 255);
}

span {
    height: 12%;
    text-align: left;
    margin: 0; padding: 0;
   font-size: .9em;
   color: rgb(121, 119, 119);
   font-weight: 200;
   margin: 3px;
 
}
span:nth-child(1) {
    color: rgb(0, 102, 255);
    font-size: 1.1em;
    font-weight: 600;
}



 


</style>
