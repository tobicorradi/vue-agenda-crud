<template>
  <form class="form" @submit.prevent>
    <div class="form__input-block">
      <label class="form__label" for="">Nombre:</label>
      <input
        required
        v-model="name"
        type="text"
        placeholder="Carlos Rodriguez"
        name="name"
        id="name"
        class="form__input"
      />
    </div>
    <div class="form__input-block">
      <label class="form__label" for="">Categoría:</label>
      <select
        required
        class="form__input"
        name="category"
        id="category"
        v-model="category"
      >
        <option value="Neutro" selected="true">Selecciona una categoría</option>
        <option
          v-for="category in categories"
          :key="category.categoryValue"
          :value="category.categoryValue"
        >
          {{ category.name }}
        </option>
      </select>
    </div>
    <div class="form__input-block">
      <label class="form__label" for="">Número:</label>
      <input
        required
        v-model="number"
        type="number"
        name="number"
        id="number"
        placeholder="1559050654"
        class="form__input"
      />
    </div>
    <button @click="addContact" type="submit">Agregar</button>
  </form>
</template>
<script>
export default {
  name: "Form",
  props: {
    categories: Object,
    contacts: Object,
  },
  data() {
    return {
      name: "",
      category: "",
      number: null,
    };
  },
  methods: {
    addContact() {
      if (this.name && this.category && this.number) {
        let newContact = {
          id: this.contacts.length + 1,
          name: this.name,
          category: this.category,
          number: this.number,
        };
        this.$emit("addContact", newContact);
      }
      return false;
    },
  },
};
</script>
<style>
.form {
  margin-bottom: 15px;
}
.form__input-block {
  margin-bottom: 10px;
}
.form__input-block * {
  display: block;
}
.form__input {
  width: 100%;
  padding: 10px;
}
.form__label {
  margin-bottom: 5px;
}
</style>