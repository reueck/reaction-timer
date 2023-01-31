

<template>
  <header>
    <h1>Reakcją tajmer</h1>
    <p>Intro xD</p>
  
  </header>

  <main>
    <TheWelcome />
  </main>
</template>

<script>
</script>


<style lang="scss" scoped>


header {
  display: flex;
  flex-direction: column;
  align-items: center;
  padding: var(--section-gap);
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
  }
}
</style>
