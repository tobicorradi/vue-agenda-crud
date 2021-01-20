<template>
  <div class="container">
    <h1>Agenda Personal</h1>
    <Form
      @addContact="addContact"
      :contacts="contacts"
      :categories="categories"
    />
    <Table :contacts="contacts" />
  </div>
</template>

<script>
import Table from "./components/Table";
import Form from "./components/Form";
export default {
  name: "App",
  components: {
    Table,
    Form,
  },
  data() {
    return {
      favourites: [],
      categories: [
        {
          name: "Amigo",
          categoryValue: "Amigo",
          selected: false,
        },
        {
          name: "Familia",
          categoryValue: "Familia",
          selected: false,
        },
        {
          name: "Trabajo",
          categoryValue: "Trabajo",
          selected: true,
        },
        {
          name: "Universidad",
          categoryValue: "Universidad",
          selected: false,
        },
      ],
      contacts: [
        {
          id: 1,
          name: "Tobías Corradi",
          category: "Amigo",
          number: 1559050654,
        },
        {
          id: 2,
          name: "Carlos",
          category: "Trabajo",
          number: 45860654,
        },
      ],
    };
  },
  methods: {
    addContact(newContact) {
      this.contacts.push({
        id: this.contacts.length + 1,
        name: newContact.name,
        category: newContact.category,
        number: newContact.number,
      });
    },
  },
};
</script>

<style>
* {
  box-sizing: border-box;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  margin-top: 60px;
}
.container {
  max-width: 800px;
  padding: 30px;
  margin: 0 auto;
}
</style>
