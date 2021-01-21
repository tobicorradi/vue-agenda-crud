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
    <tr
      class="table__content"
      v-for="(contact, index) in contacts"
      :key="contact.id"
    >
      <td><span class="form__mobile-label">ID</span>{{ contact.id }}</td>
      <td><span class="form__mobile-label">Nombre</span>{{ contact.name }}</td>
      <td>
        <span class="form__mobile-label">Categoría</span>{{ contact.category }}
      </td>
      <td>
        <span class="form__mobile-label">Número</span>{{ contact.number }}
      </td>
      <td><button class="btn form__button">Favorito</button></td>
      <td>
        <button @click="isEditing(index)" class="btn form__button">
          Editar
        </button>
      </td>
      <td>
        <button @click="deleteContact(index)" class="btn form__button">
          Eliminar
        </button>
      </td>
    </tr>
  </table>
</template>
<script>
export default {
  name: "Table",
  props: {
    contacts: Object,
  },
  methods: {
    deleteContact(index) {
      this.$emit("deleteContact", index);
    },
    isEditing(index) {
      this.$emit("isEditing", index);
    },
  },
};
</script>
<style>
table {
  width: 100%;
  border-spacing: 11px;
}
.form__mobile-label {
  display: none;
}
@media (max-width: 768px) {
  .form__mobile-label {
    display: block;
    font-size: 12px;
    color: #828282;
    font-weight: 100;
  }
  .table__header {
    display: none;
  }
  td {
    display: block;
    margin-bottom: 10px;
    display: flex;
    justify-content: space-between;
    font-size: 16px;
    font-weight: 700;
  }
  tr {
    display: block;
    margin-bottom: 30px;
    padding: 18px;
    box-shadow: rgba(0, 0, 0, 0.15) 1.95px 1.95px 2.6px;
  }
}
.table__header th {
  text-align: left;
  font-size: 11px;
  font-weight: 700;
  color: #a0a0a0;
}
td {
  font-size: 15px;
}
.table__content {
  margin-bottom: 10px;
}
</style>