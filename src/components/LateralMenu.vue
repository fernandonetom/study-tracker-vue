<template>
  <header class="is-flex is-align-items-center	is-justify-content-flex-start is-flex-direction-column">
    <h1>
      <img class="logo" src="../assets/logo.png" alt="Vue Logo" />
    </h1>
    <h1 class="is-size-3">
      Study Tracker
    </h1>
  </header>
</template>

<style scoped>
header {
  padding: 1rem;
  background: #adb6bf;
  width: 100%;
  height: 100vh;

  .logo {
    max-width: 170px;
  }
}

@media only screen and (max-width: 768px) {
  header {
    padding: 2.5rem;
    height: auto;
  }
}
</style>
