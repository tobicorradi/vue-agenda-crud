<template>
  <table>
    <tr class="table__header">
      <th>ID</th>
      <th>Nombre</th>
      <th>Categoría</th>
      <th>Numero</th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
    <tr v-for="contact in contacts" :key="contact.id">
      <td><span class="form__mobile-label">ID</span>{{ contact.id }}</td>
      <td><span class="form__mobile-label">Nombre</span>{{ contact.name }}</td>
      <td>
        <span class="form__mobile-label">Categoría</span>{{ contact.category }}
      </td>
      <td>
        <span class="form__mobile-label">Número</span>{{ contact.number }}
      </td>
      <td><button class="form__button">Favorito</button></td>
      <td><button class="form__button">Editar</button></td>
      <td><button class="form__button">Eliminar</button></td>
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
<style>
table {
  width: 100%;
}
.form__mobile-label {
  display: none;
}
.form__button {
  padding: 10px 30px;
}
@media (max-width: 768px) {
  .form__mobile-label {
    display: block;
  }
  .table__header {
    display: none;
  }
  td {
    display: block;
    margin-bottom: 10px;
    display: flex;
    justify-content: space-between;
  }
  tr {
    display: block;
    margin-bottom: 15px;
  }
  tr:nth-child(odd) {
    background-color: #f3f3f3;
  }
  .form__button {
    width: 100%;
  }
}
</style>