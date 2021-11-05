<template>
    <li> 
      {{ title }} 
      <button @click='$emit("removeTask", id)'>Eliminar</button> 
    </li>

</template>

<script>
export default {
  name: 'HelloWorld',
  props: {
    id: String,
    title: String
  },
  emits: ['removeTask']
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
li {
  list-style: none;
}

</style>
