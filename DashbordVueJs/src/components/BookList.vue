<script setup>
import BookItems from "./BookItems.vue";

const props = defineProps({
  table: Array,
});
const emit = defineEmits(["delete"]);

function update(book) {
  book.Statut = !book.Statut;
}
</script>

<template>
  <div>
    <h3>Ajout des livres enregistrés</h3>
    <ul>
      <BookItems
        v-for="(book, index) in table" 
        :key="index"
        :book="book"
        :index="index"
        @delete="(i) => emit('delete', i)"
        @update="update"
      />
    </ul>
  </div>
</template>

<style scoped>
div { margin-top: 30px; color: white; }
h3 {
  font-size: 1.5rem;
  margin-bottom: 20px;
  border-left: 5px solid #1a222d;
  padding-left: 15px;
}
ul { list-style: none; padding: 0; }
</style>