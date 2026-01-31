<script setup>
const props = defineProps({
  book: Object,
  index: Number
});

const emit = defineEmits(["delete", "update"]);

function toggleStatus() {
  emit("update", props.book);
}
</script>

<template>
  <li>
    <span>
      {{ index + 1 }} -- {{ book.Title }} -- {{ book.Auteur }} --
      {{ book.Annee }} -- {{ book.category }}
    </span>
    <button @click="emit('delete', index)">❌</button>
    
    <p :class="book.Statut ? 'status-a-lire' : 'status-lu'">
      {{ book.Statut ? 'A Lire' : 'Lu' }}
    </p>

    <button v-if="book.Statut" @click="toggleStatus" type="button">
      Marquer comme lu ✔
    </button>
    <button v-else type="button" @click="toggleStatus">
      Marquer non lu
    </button>
  </li>
</template>

<style scoped>
ul {
  list-style: none;
  padding: 0;
}

li {
  background-color: rgba(255, 255, 255, 0.95);
  margin-bottom: 15px;
  padding: 20px;
  border-radius: 10px;
  color: #1a222d;
  display: grid;
  grid-template-columns: 1fr auto;
  gap: 10px;
  align-items: center;
  box-shadow: 0 4px 15px rgba(0, 0, 0, 0.2);
  transition: transform 0.2s;
}

li:hover {
  transform: scale(1.02);
}

span {
  font-weight: 600;
  font-size: 1.1rem;
  grid-column: 1;
}

li > button:first-of-type {
  background: none;
  border: none;
  font-size: 1.2rem;
  cursor: pointer;
  grid-column: 2;
  grid-row: 1;
  transition: opacity 0.2s;
}

li > button:first-of-type:hover {
  opacity: 0.6;
}

p {
  font-size: 0.9rem;
  font-weight: bold;
  text-transform: uppercase;
  margin: 5px 0;
  grid-column: 1;
}

.status-lu { 
  color: #2ecc71 !important; 
}

.status-a-lire { 
  color: #e67e22 !important; 
}

button[type="button"] {
  grid-column: 1 / span 2;
  padding: 8px;
  border: 1.5px solid #1a222d;
  background: transparent;
  color: #1a222d;
  border-radius: 5px;
  font-weight: bold;
  cursor: pointer;
  transition: all 0.3s ease;
  font-size: 0.85rem;
}

button[type="button"]:hover {
  background-color: #1a222d;
  color: white;
}
</style>