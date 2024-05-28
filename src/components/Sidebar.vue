<template>
    <aside class="sidebar">
      <h1>Notes</h1>
      <div class="notes-list">
        <NoteItem
          v-for="note in notes"
          :key="note.id"
          :note="note"
          @selectNote="selectNote"
        />
      </div>
      <button class="create-note" @click="createNote">Cree note</button>
    </aside>
  </template>
  
  <script>
  import NoteItem from './NoteItem.vue';
  
  export default {
    components: {
      NoteItem
    },
    props: {
      notes: {
        type: Array,
        required: true
      }
    },
    methods: {
      createNote() {
        this.$emit('createNote');
      },
      selectNote(note) {
        this.$emit('selectNote', note);
      }
    }
  }
  </script>
  
  <style scoped>
  .sidebar {
    width: 300px;
    background-color: #fff;
    padding: 20px;
    border-right: 1px solid #ddd;
    overflow-y: auto;
  }
  
  h1 {
    font-size: 1.5em;
    margin-bottom: 20px;
  }
  
  .create-note {
    display: block;
    width: 100%;
    padding: 10px;
    margin-top: 20px;
    background-color: #007bff;
    color: #fff;
    border: none;
    cursor: pointer;
    border-radius: 4px;
  }
  </style>
  