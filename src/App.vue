<script setup lang="ts">
import { ref } from 'vue'

const data = ref(['akash', 'jawad', 'ratul', 'wakil'])
let inputValue = ''

const handleClick = () => {
  console.log('first')
  data.value = [...data.value, inputValue]
}
</script>

<template>
  <main class="flex flex-col items-center justify-center h-screen">
    <div>
      <template v-for="item in data" :key="item">
        <h1
          class="p-2 border-2 m-2 rounded-2xl bg-slate-400 text-xl font-bold text-center"
          :class="item === 'meraj bhai' ? 'bg-red-500' : ''"
        >
          {{ item }}
        </h1>
      </template>
    </div>
    <input type="text" v-model="inputValue" placeholder="Enter a name" class="border-2 p-2" />
    <button
      class="p-2 text-lg font-bold bg-green-500 hover:bg-green-400 rounded-2xl mt-4"
      @click="handleClick"
    >
      click here
    </button>
  </main>
</template>

<style scoped>
header {
  line-height: 1.5;
  max-height: 100vh;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

nav {
  width: 100%;
  font-size: 12px;
  text-align: center;
  margin-top: 2rem;
}

nav a.router-link-exact-active {
  color: var(--color-text);
}

nav a.router-link-exact-active:hover {
  background-color: transparent;
}

nav a {
  display: inline-block;
  padding: 0 1rem;
  border-left: 1px solid var(--color-border);
}

nav a:first-of-type {
  border: 0;
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  .logo {
    margin: 0 2rem 0 0;
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }

  nav {
    text-align: left;
    margin-left: -1rem;
    font-size: 1rem;

    padding: 1rem 0;
    margin-top: 1rem;
  }
}
</style>
