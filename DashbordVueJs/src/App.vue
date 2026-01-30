<script setup>
import { ref } from "vue";
import BookForm from "./components/BookForm.vue";
import BookList from "./components/BookList.vue";

const view = ref("");
function open(e) {
  console.log(e);
  view.value = e;
}
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
    </div>
  </main>
</template>
<style>
* {
  padding: 0;
  margin: 0;
  box-sizing: border-box;
}
main {
  display: flex;
  /* flex-direction: row; */
  justify-content: space-around;
  gap: 200px;
  margin: auto;
  width: 100%;
}
.listBook {
  display: grid;
  grid-template-columns: auto;
  gap: 12px;
  margin: auto;
}
.container_ListBook {
  background-color: midnightblue;
  width: 50%;
  height: 500px;
  text-align: center;
  margin-left: -100px;
  margin-top: -33px;
}
.acceuilContainer {
  background-color: gray;
  width: 50%;
  height: 500px;
  margin-top: -33px;
}
button {
  cursor: pointer;
}
</style>
