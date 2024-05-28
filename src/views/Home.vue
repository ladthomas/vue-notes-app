<template>
  <div class="app-container">
    <Sidebar
      :notes="notes"
      @createNote="createNote"
      @selectNote="selectNote"
    />
    <main class="content">
      <NoteDetail
        v-if="selectedNote"
        :note="selectedNote"
        @deselectNote="deselectNote"
        @saveNote="saveNote"
        @deleteNote="deleteNote"
      />
      <div v-else class="select-note">
        Select a note to view its content
      </div>
    </main>
  </div>
</template>

<script>
import Sidebar from '../components/Sidebar.vue';
import NoteDetail from '../components/NoteDetail.vue';

export default {
  components: {
    Sidebar,
    NoteDetail
  },
  data() {
    return {
      notes: [],
      selectedNote: null
    }
  },
  created() {
    this.loadNotes();
    this.loadSelectedNote();
  },
  watch: {
    '$route.params.id': 'loadSelectedNote'
  },
  methods: {
    loadNotes() {
      const savedNotes = JSON.parse(localStorage.getItem('notes') || '[]');
      this.notes = savedNotes;
    },
    saveNotes() {
      localStorage.setItem('notes', JSON.stringify(this.notes));
    },
    createNote() {
      const newNote = {
        id: Date.now(),
        title: 'Nouvelle note',
        content: '',
        created: new Date().toISOString(),
        updated: new Date().toISOString()
      };
      this.notes.push(newNote);
      this.saveNotes();
      this.$router.push(`/note/${newNote.id}`);
    },
    selectNote(note) {
      this.$router.push(`/note/${note.id}`);
    },
    deselectNote() {
      this.$router.push('/');
    },
    loadSelectedNote() {
      const noteId = this.$route.params.id;
      if (noteId) {
        this.selectedNote = this.notes.find(note => note.id === Number(noteId));
      } else {
        this.selectedNote = null;
      }
    },
    saveNote() {
      if (this.selectedNote) {
        this.selectedNote.updated = new Date().toISOString();
        this.saveNotes();
      }
    },
    deleteNote() {
      if (this.selectedNote) {
        this.notes = this.notes.filter(n => n.id !== this.selectedNote.id);
        this.saveNotes();
        this.selectedNote = null;
        this.$router.push('/');
      }
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
.app-container {
  display: flex;
  height: 100vh;
  background-color: #f0f0f5;
}

.content {
  flex-grow: 1;
  padding: 20px;
  background-color: #fff;
  overflow-y: auto;
}

.select-note {
  margin: auto;
  color: #777;
}
</style>
