<template>
  <div class="note-detail">
    <header class="note-header">
      <button @click="goBack" class="back-button">Retour</button>
    </header>
    <div v-if="note" class="note-content">
      <input v-model="note.title" class="note-title" placeholder="Title" />
      <textarea v-model="note.content" class="note-body" placeholder="Écrivez votre note ici..."></textarea>
      <p class="note-meta">Created: {{ formatDate(note.created) }}</p>
      <p class="note-meta">Last updated: {{ formatDate(note.updated) }}</p>
      <div class="buttons">
        <button @click="saveNote" class="save-note">Sauvegarde note </button>
        <button @click="deleteNote" class="delete-note">Supprime note</button>
      </div>
    </div>
    <div v-else class="select-note">
        Sélectionnez une note pour en afficher le contenu
    </div>
  </div>
</template>

<script>
export default {
  props: {
    note: {
      type: Object,
      required: false
    }
  },
  methods: {
    goBack() {
      this.$emit('deselectNote');
    },
    saveNote() {
      this.$emit('saveNote');
    },
    deleteNote() {
      this.$emit('deleteNote');
    },
    formatDate(date) {
      const options = {
        year: 'numeric',
        month: '2-digit',
        day: '2-digit',
        hour: '2-digit',
        minute: '2-digit'
      };
      return new Date(date).toLocaleDateString(undefined, options);
    }
  }
}
</script>

<style scoped>
.note-detail {
  padding: 20px;
  flex-grow: 1;
  background-color: #f9f9f9;
  display: flex;
  flex-direction: column;
  border-left: 1px solid #ddd;
}

.note-header {
  display: flex;
  justify-content: flex-start;
  align-items: center;
  margin-bottom: 20px;
}

.back-button {
  background-color: #007bff;
  color: white;
  border: none;
  padding: 10px 20px;
  border-radius: 4px;
  cursor: pointer;
  transition: background-color 0.3s;
}

.back-button:hover {
  background-color: #0056b3;
}

.note-content {
  display: flex;
  flex-direction: column;
  height: 100%;
}

.note-title {
  font-size: 1.5em;
  margin-bottom: 10px;
  background-color: #fff;
  color: #333;
  border: 1px solid #ddd;
  padding: 10px;
  border-radius: 4px;
  box-shadow: inset 0 1px 3px rgba(0, 0, 0, 0.1);
  width: 100%;
  box-sizing: border-box;
}

.note-body {
  flex-grow: 1;
  margin-bottom: 10px;
  font-size: 1em;
  padding: 10px;
  border: 1px solid #ddd;
  border-radius: 4px;
  background-color: #fff;
  color: #333;
  box-shadow: inset 0 1px 3px rgba(0, 0, 0, 0.1);
  resize: none;
  width: 100%;
  height: calc(100vh - 250px); /* Adjust based on your layout */
  box-sizing: border-box;
}

.note-meta {
  font-size: 0.8em;
  color: #777;
  margin-bottom: 5px;
}

.buttons {
  display: flex;
  gap: 10px;
}

.save-note,
.delete-note {
  padding: 10px 20px;
  color: #fff;
  border: none;
  cursor: pointer;
  border-radius: 4px;
  transition: background-color 0.3s;
}

.save-note {
  background-color: #28a745;
}

.save-note:hover {
  background-color: #218838;
}

.delete-note {
  background-color: #d9534f;
}

.delete-note:hover {
  background-color: #c9302c;
}

.select-note {
  margin: auto;
  color: #777;
}
</style>
