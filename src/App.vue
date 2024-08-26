<script setup>
import { ref } from 'vue';
 
  const showForm = ref(false)
  const newMemo = ref("")
  const memos = ref([])

  const toggleDisplay = () => {
    showForm.value = !showForm.value
  }

  const addMemo = () => {
    memos.value.push({
      id: Date.now(),
      memo: newMemo.value,
      date: new Date().toLocaleDateString('en-GB'),
      backgroundColor: generateColor(),
    })

    newMemo.value = ''
    showForm.value = false
  }

  const generateColor = () => {
    return `#${Math.floor(Math.random() * 16777215).toString(16)}`
  }

</script>

<template>
  <main>
    <div class="container">
      <header>
        <h1 class="header-title">Memo</h1>
        <button class="header-button" @click="toggleDisplay">+</button>
      </header>
      <div class="card-container">
        <div v-for="(memo, index) in memos" :key="index" class="card" :style="{backgroundColor: memo.backgroundColor}">
        <p class="card-content">{{ memo.memo }}</p>
        <p class="card-date">{{ memo.date }}</p>
      </div>
      </div>
    </div>
    <div class="form-overlay" v-if="showForm">
      <div class="form-modal">
        <button class="form-close-btn" @click="toggleDisplay">&times;</button>
        <textarea v-model="newMemo" name="memo" id="memo" cols="30" rows="10"></textarea>
        <button @click="addMemo" class="form-save-btn">save</button>
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

.card-container {
  display: flex;
  flex-wrap: wrap;
  gap: 20px;
}

.card {
  width: 225px;
  height: 225px;
  padding: 10px;
  background-color: gray;
  border-radius: 5%;
  margin-bottom: 20px;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
}

.form-overlay {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, 0.77);
  z-index: 10;
  display: flex;
  align-items: center;
  justify-content: center;
}

.form-modal {
  width: 420px;
  background-color: white;
  border-radius: 10px;
  padding: 30px;
  position: relative;
  display: flex;
  flex-direction: column;
}

.form-save-btn {
  padding: 10px 20px;
  font-size: 20px;
  width: 100%;
  background-color: gray;
  border: none;
  cursor: pointer;
  border-radius: 5px;
  margin-top: 15px;
  color: white;
}

.form-close-btn {
  position: absolute;
  top: 5px;
  right: 10px;
  width: 30px;
  height: 30px;
  background-color: transparent;
  border: none;
  font-size: 25px;
  cursor: pointer;
}
</style>
