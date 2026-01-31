<script setup>
import { ref, computed } from "vue";
import BookList from "./BookList.vue";
const bookTitle = ref("");
const bookAuteur = ref("");
const bookAnnee = ref("");
const bookCategory = ref("");
const booklu = ref("Lu");

const table = ref([]);

const emit = defineEmits(["add"]);

function deleteBtn(index) {
  table.value.splice(index, 1);
}

function submitForm() {
  const addBooks = {
    Title: bookTitle.value,
    Auteur: bookAuteur.value,
    Annee: bookAnnee.value,
    Category: bookCategory.value,
    Statut: booklu.value,
  };
  table.value.push(addBooks);
  console.log(table);
  bookAnnee.value = "";
  bookAuteur.value = "";
  bookCategory.value = "";
  bookTitle.value = "";
  booklu.value = "";
  emit("add", addBooks);
}
const canAdd = computed(() => {
  return (
    bookTitle.value.trim() &&
    bookAuteur.value.trim() &&
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
    <input v-model="bookAnnee" type="date" placeholder="Year of the book" />
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
    <BookList :table="table" @delete="deleteBtn" />
  </form>
</template>
<style scoped>
/* Conteneur du formulaire */
form {
  max-width: 500px;
  background-color: rgba(255, 255, 255, 0.15); /* Effet verre (Glassmorphism) */
  backdrop-filter: blur(10px);
  padding: 30px;
  border-radius: 15px;
  border: 1px solid rgba(255, 255, 255, 0.2);
  box-shadow: 0 8px 32px rgba(0, 0, 0, 0.3);
}

/* Labels */
label {
  display: inline-block;
  color: #ffffff;
  font-weight: 600;
  margin-bottom: 8px;
  text-transform: uppercase;
  font-size: 0.85rem;
  letter-spacing: 1px;
}

/* Champs de saisie (Inputs) */
input {
  width: 100%;
  padding: 12px 15px;
  margin-bottom: 20px;
  border: 1px solid rgba(255, 255, 255, 0.3);
  border-radius: 8px;
  background-color: rgba(
    255,
    255,
    255,
    0.9
  ); /* Fond blanc cassé pour l'écriture */
  color: #1a222d;
  font-size: 1rem;
  transition: all 0.3s ease;
}

input:focus {
  outline: none;
  border-color: #f1f3f5;
  box-shadow: 0 0 8px rgba(255, 255, 255, 0.5);
}

/* Bouton d'envoi */
button {
  width: 100%;
  padding: 15px;
  background-color: #1a222d; /* Rappel de la couleur de la sidebar */
  color: white;
  border: none;
  border-radius: 8px;
  font-size: 1rem;
  font-weight: bold;
  text-transform: uppercase;
  cursor: pointer;
  transition:
    transform 0.2s,
    background-color 0.3s;
  margin-top: 10px;
}

button:hover:not(:disabled) {
  background-color: #2c3e50;
  transform: translateY(-2px);
}

button:disabled {
  background-color: #64748b;
  cursor: not-allowed;
  opacity: 0.6;
}

/* Espace pour le composant de liste en dessous */
form > :last-child {
  margin-top: 30px;
  border-top: 1px solid rgba(255, 255, 255, 0.2);
  padding-top: 20px;
}
</style>
