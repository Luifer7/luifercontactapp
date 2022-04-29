

<template>
  <div id="search-container">
    <input placeholder="Buscar" class="buscar" type="text" v-model="query" v-on:input="$emit('query-change', query)">
    <svg xmlns="http://www.w3.org/2000/svg" width="12" height="12" fill="currentColor" class="bi bi-search input-icon password" viewBox="0 0 16 16">
  <path d="M11.742 10.344a6.5 6.5 0 1 0-1.397 1.398h-.001c.03.04.062.078.098.115l3.85 3.85a1 1 0 0 0 1.415-1.414l-3.85-3.85a1.007 1.007 0 0 0-.115-.1zM12 6.5a5.5 5.5 0 1 1-11 0 5.5 5.5 0 0 1 11 0z"/>
</svg>
  </div>
</template>

<script>
export default {
  name: 'MySearchCliente',
  data () {
      return {
          query: ''
      }
  }
 
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

#search-container {
  height: 100%;
  width: 300px;
  display: flex;
  justify-content: center;
  align-items: center;
  border-radius: 10px;
   position: relative;
  
}

.buscar {
  border-radius: 10px;
  height: 80%;
  width: 100%;
  outline: none;
  border: none;
  background: rgba(232, 237, 238, 0.918);
  position: relative;
   box-sizing: border-box;
  color: #191919;
  padding: 15px 15px 15px 35px;
    
}

.buscar::placeholder {
  margin-left: 20px;
}

.input-icon {
  color: #191919;
  position: absolute;
  width: 14px;
  height: 14px;
  left: 12px;
  top: 50%;
  transform: translateY(-50%);
}

.input-icon.password {
  left: unset;
  right: 12px;
}

</style>
