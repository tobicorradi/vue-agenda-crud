<template>
  <table>
    <tr>
      <th>ID</th>
      <th>Nombre</th>
      <th>Categoría</th>
      <th>Numero</th>
      <th>Favorito</th>
    </tr>
    <tr v-for="contact in contacts" :key="contact.id">
      <td>{{ contact.id }}</td>
      <td>{{ contact.name }}</td>
      <td>{{ contact.category }}</td>
      <td>{{ contact.number }}</td>
      <td><button>Agregar a favorito</button></td>
    </tr>
  </table>
</template>
<script>
export default {
  name: "Table",
  props: {
    contacts: Object,
  },
};
</script>
<style lang="stylus">

</style>