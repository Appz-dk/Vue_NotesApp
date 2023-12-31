<script setup>
import { ref } from "vue"

const showModal = ref(false)
const newNote = ref("")
const notes = ref([])


function getRandomColor() {
  return "hsl(" + Math.random() * 360 + ", 100%, 75%)";
}

const addNoteHandler = () => {
  if (!newNote.value) return

  notes.value.push({ 
    id: `${Math.ceil(Math.random()*1000000)}-${notes.value.length}`,
    text: newNote.value,
    date: new Date(),
    backgroundClr: getRandomColor()
  })
  showModal.value = false
  newNote.value = ""
} 

const deleteNoteHandler = (id) => {
  notes.value = notes.value.filter(note => note.id !== id )
}

</script>

<template>
  <main>
    <div v-if="showModal" class="modal-container">
      <div class="overlay">
      </div>
      <div class="modal">
        <textarea v-model.trim="newNote" id="note" name="note" cols="20" rows="10" ></textarea>
        <button @click="addNoteHandler">Add Note</button>
        <button @click="showModal = false" class="close">Close</button>
      </div>
    </div>
    <div class="container">
      <header>
        <h1>Notes</h1>
        <button @click="showModal = true">+</button>
      </header>
      <div class="cards-container">
        <div class="card" v-for="note in notes" :key="note.id" :style="{backgroundColor: note.backgroundClr}">
          <p class="main-text">{{ note.text }}</p>
          <div class="card-footer">
            <p class="date">{{ note.date.toLocaleDateString() }}</p>
            <button @click="deleteNoteHandler(note.id)">Delete</button>
          </div>
        </div>
      </div>
    </div>
  </main>
</template>

<style scoped>
  main {
    width: 100%;
    height: 100%;
  }
  .container {
    max-width: 1000px;
    margin: 0 auto;
    padding: 10px;
  } 

  header {
    display: flex;
    justify-content: space-between;
    align-items: center;
    color: white;
  }

  h1 {
    font-size: 2.5rem;
  }

  button {
    background-color: #1e1e1e;
    outline: none;
    border: none;
    border-radius: 8px;
    padding: .5rem 1.25rem;
    color: white;
    cursor: pointer;
  }

  button:hover {
    outline: 1px solid #eee
  }

  header button {
    font-size: 1.25rem;
  }

  p {
    margin: 0;
  }

  .card {
    width: 225px;
    aspect-ratio: 1;
    background-color: #234231;
    border-radius: 8px;
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    padding: 1rem;
  }

  .date {
    font-size: .85rem;
    font-weight: bold;
  }

  .cards-container {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    row-gap: 2rem;
  }

  .overlay {
    position: absolute;
    inset: 0;
    width: 100%;
    height: 100%;
    opacity: .15;
    background-color: white;
    z-index: 10;
    display: grid;
    place-items: center;
  }
  .modal {
    width: 600px;
    background-color: #2f2f2f;
    z-index: 100;
    border-radius: 8px;
    padding: 1rem;
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    display: flex;
    flex-direction: column;
    gap: .5rem;
  }

  .card-footer {
    display: flex;
    justify-content: space-between;
    align-items: center;
  }

  .card-footer button {
    background-color: #cd4d4d
  }
  .modal textarea {
    padding: .5rem;
    resize: none;
  }

  .modal .close {
    background-color: #cd4d4d;
  }
</style>
