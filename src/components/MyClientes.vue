

<template>
  <div class="box-items" >
      <div  v-bind:key="cliente.id" v-for="cliente in clientesList" >
         <MyClientesItem v-bind:cliente="cliente" v-on:delete-cliente="$emit('delete-cliente', cliente.id)"/>
      </div>
  </div>
</template> 



<script>
import MyClientesItem from './MyClientesItem';

export default {
  name: 'MyClientes',
  props: ['clientesList'],
  components: {MyClientesItem}

}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  .box-items {
     border-radius: 5% ;
     background: rgba(232, 237, 238, 0.918);
     padding: 20px;
  }

</style>
