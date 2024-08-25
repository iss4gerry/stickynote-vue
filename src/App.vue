<template>
  <main>
    <div class="container">
      <header>
        <h1 class="header-title">Memo</h1>
        <button class="header-button">+</button>
      </header>
      <div>
        [card]
      </div>
    </div>
  </main>
</template>

<style scoped>
main {
  height: 100vh;
  width:100vw;
}

.container {
  max-width: 900px;
  padding: 10px;
  margin: 0 auto;
}

header {
  display: flex;
  justify-content: space-between;
  align-items: center
}

.header-title {
  font-size: 48px;
  font-weight: bold;
  margin-bottom: 25px;
}

.header-button {
  border: none;
  padding: 10px;
  width: 40px;
  height: 40px;
  cursor: pointer;
  border-radius: 100%;
  background-color: gray;
  color: white;
}
</style>
