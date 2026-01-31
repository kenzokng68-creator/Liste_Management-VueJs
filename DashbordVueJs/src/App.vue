<script setup>
import { ref } from "vue";
import BookForm from "./components/BookForm.vue";
import BookItems from "./components/BookItems.vue";
const view = ref("");
function open(e) {
  console.log(e);
  view.value = e;
}
const actifsCount = computed(() => {
  return table.value.filter((p) => p.etat === "Actif").length;
});
</script>

<template>
  <main>
    <div class="container_ListBook">
      <h2>Dashboard</h2>
      <div class="listBook">
        <button @click="open('Home')">Home</button>
        <button @click="open('Book')">Book</button>
        <button @click="open('Users')">Users</button>
        <button @click="open('FormUsers')">FormUsers</button>
        <button @click="open('Orders')">Orders</button>
        <button @click="open('Reports')">Reports</button>
        <button @click="open('Settings')">Settings</button>
      </div>
    </div>
    <div class="acceuilContainer">
      <h1>Acceuil</h1>
      <BookForm v-if="view === 'Book'"></BookForm>
      <BookItems :table="table" :actifsCount="actifsCount" />
    </div>
  </main>
</template>

<style>
* {
  padding: 0;
  margin: 0;
  box-sizing: border-box;
}

#app {
  display: block !important;
  padding: 0 !important;
  width: 100% !important;
  max-width: none !important;
}

main {
  display: flex !important;
  min-height: 100vh;
  width: 100vw;
}

/* --- DASHBOARD (SIDEBAR) --- */
.container_ListBook {
  width: 350px;
  background-color: #1a222d;
  min-height: 100vh;
  display: flex;
  flex-direction: column;
  padding-top: 20px;
  z-index: 10;
}

.container_ListBook h2 {
  color: white;
  font-size: 32px;
  font-weight: bold;
  padding: 20px 30px;
  width: 100%;
}

.listBook {
  display: flex;
  flex-direction: column;
  gap: 8px;
}

.listBook button {
  background-color: #f1f3f5;
  border: none;
  padding: 18px 30px;
  text-align: left;
  font-size: 18px;
  cursor: pointer;
  width: 100%;
  color: #333;
  transition: background-color 0.2s;
}

.listBook button:hover {
  background-color: #e2e6ea;
}

/* --- ACCUEIL (Avec l'image en fond uniquement ici) --- */
.acceuilContainer {
  flex: 1;
  padding: 40px;
  /* L'image est appliquée ici au lieu du body */
  background-image: url("premium_photo-1682284079664-c90a1603733b.avif");
  background-size: cover;
  background-position: center;
  background-repeat: no-repeat;
  color: white; /* Texte en blanc pour être lisible sur l'image */
}

.acceuilContainer h1 {
  font-size: 32px;
  text-shadow: 2px 2px 8px rgba(0, 0, 0, 0.7); /* Ombre plus forte pour détacher le texte du fond */
}
</style>
