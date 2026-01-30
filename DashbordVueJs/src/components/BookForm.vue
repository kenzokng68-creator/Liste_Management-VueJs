<script setup>
import { ref, computed } from "vue";

const bookTitle = ref("");
const bookAuteur = ref("");
const bookAnnee = ref("");
const bookCategory = ref("");

// // // VALIDATION : Le bouton "Ajouter" ne s'active que si tout est rempli
// const canAdd = computed(() => {
//   return usermail.value.trim() && username.value.trim() && status.value.trim();
// });
const table = ref ([]);
const emit = defineEmits(["add"]);
function submitForm() {
  const addBooks = {
    Title: bookTitle.value,
    Auteur: bookAuteur.value,
    Annee: bookAnnee.value,
    Category: bookCategory.value,
  };
  table.value.push(addBooks)
  console.log(table);
  bookAnnee.value = "";
  bookAuteur.value = "";
  bookCategory.value = "";
  bookTitle.value = "";
  emit("add", addBooks);
}
const canAdd = computed(() => {
  return (
    bookTitle.value.trim() &&
    bookAuteur.value.trim() &&
    bookAnnee.value.trim() &&
    bookCategory.value.trim()
  );
});
</script>
<template>
  <form @submit.prevent="submitForm">
    <label for="">Title of book</label>
    <br />
    <input v-model="bookTitle" type="text" placeholder="Title of book" />
    <br />
    <label for="">Name of author's</label>
    <br />
    <input v-model="bookAuteur" type="text" placeholder="Name of author's" />
    <br />
    <label for="">year of the work</label>
    <br />
    <input v-model="bookAnnee" type="text" placeholder="Year of the book" />
    <br />
    <label for="">category of book</label>
    <br />
    <input
      v-model="bookCategory"
      type="text"
      placeholder="Enter this category"
    />
    <br />
    <button :disabled="!canAdd">Send</button>
  </form>
</template>
<script></script>
