<template>
  <table v-if="contacts.length">
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
      <td>
        <span class="form__mobile-label">ID</span><span>{{ contact.id }}</span>
      </td>
      <td>
        <span class="form__mobile-label">Nombre</span
        ><span v-if="!contact.editing">{{ contact.name }}</span>
        <input v-else type="text" v-model="contact.name" />
      </td>
      <td>
        <span class="form__mobile-label">Categoría</span
        ><span v-if="!contact.editing">{{ contact.category }}</span>
        <select v-model="contact.category" v-else name="" id="">
          <option
            v-for="category in categories"
            :key="category.name"
            :value="category.name"
          >
            {{ category.name }}
          </option>
        </select>
      </td>
      <td>
        <span class="form__mobile-label">Número</span
        ><span v-if="!contact.editing">{{ contact.number }}</span>
        <input v-else type="number" v-model="contact.number" />
      </td>
      <td><button class="btn form__button">Favorito</button></td>
      <td v-if="!contact.editing">
        <button @click="isEditing(index)" class="btn form__button">
          Editar
        </button>
      </td>
      <td v-else>
        <button @click="doneEditing(index)" class="btn form__button">
          Confimar
        </button>
      </td>
      <td>
        <button @click="deleteContact(index)" class="btn form__button">
          Eliminar
        </button>
      </td>
    </tr>
  </table>
  <div v-else>
    <p>No tienes ningún contacto</p>
  </div>
</template>
<script>
export default {
  name: "Table",
  props: {
    contacts: Object,
    categories: Object,
  },
  methods: {
    deleteContact(index) {
      this.$emit("deleteContact", index);
    },
    isEditing(index) {
      this.$emit("isEditing", index);
    },
    doneEditing(index) {
      this.$emit("doneEditing", index);
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