<template>
  <div class="container">
    <h1>Agenda Personal</h1>
    <Form
      @addContact="addContact"
      :contacts="contacts"
      :categories="categories"
    />
    <Table
      :categories="categories"
      :contacts="contacts"
      @isEditing="isEditing"
      @doneEditing="doneEditing"
      @deleteContact="deleteContact"
    />
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
          editing: false,
        },
        {
          id: 2,
          name: "Carlos",
          category: "Trabajo",
          number: 45860654,
          editing: false,
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
        editing: false,
      });
    },
    deleteContact(index) {
      this.contacts.splice(index, 1);
    },
    isEditing(index) {
      this.contacts[index].editing = !this.contacts[index].editing;
    },
    doneEditing(index){
      this.contacts[index].editing = false
    }
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
  margin-top: 10px;
}
.container {
  max-width: 800px;
  padding: 30px;
  margin: 0 auto;
}
.btn {
  padding: 10px 30px;
  width: 100%;
  cursor: pointer !important;
}
@media (min-width: 768px) {
  .btn {
    max-width: 100px;
    font-size: 13px;
    padding: 10px 15px;
  }
}
</style>
