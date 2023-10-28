<script setup>
</script>

<template>
  <main>
    <div class="container">
      <header>
        <h1>Notes</h1>
        <button>+</button>
      </header>
      <div class="cards-container">
        <div class="card">
          <p class="main-text">Lorem ipsum dolor sit amet, consectetur adipisicing elit. In atque laudantium consequuntur adipisci dicta ducimus.</p>
          <p class="date">22/10-23</p>
        </div>
        <div class="card">
          <p class="main-text">Lorem ipsum dolor sit amet, consectetur adipisicing elit. In atque laudantium consequuntur adipisci dicta ducimus.</p>
          <p class="date">22/10-23</p>
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

  header button {
    background-color: #1e1e1e;
    outline: none;
    border: none;
    border-radius: 8px;
    padding: .5rem 1.25rem;
    color: white;
    font-size: 1.25rem;
    cursor: pointer;
  }

  header button:hover {
    outline: 1px solid #eee
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

</style>
