<!-- <script setup lang="ts">
import { ref } from 'vue'

const data = ref(['akash', 'jawad', 'ratul', 'wakil'])
let inputValue = ''

const handleClick = () => {
  console.log('first')
  data.value = [...data.value, inputValue]
}
</script> -->

<script lang="ts">
import CrossIcon from './components/icons/CrossIcon.vue'
export default {
  name: 'App',
  data() {
    return {
      friendsName: ['akash', 'jawad', 'ratul', 'wakil'],
      inputName: ''
    }
  },
  methods: {
    handleClick() {
      this.friendsName.push(this.inputName)
      //= [...this.friendsName, this.inputName]
      this.inputName = ''
    },
    deleteName(friend: string) {
      console.log(friend)
      const index = this.friendsName.indexOf(friend)
      if (index > -1) this.friendsName.splice(index, 1)
    }
  },
  components: {
    CrossIcon
  }
}
</script>

<template>
  <main class="flex flex-col items-center justify-center h-screen mt-10">
    <template v-for="friend in friendsName" :key="friend">
      <div class="relative">
        <p
          class="p-2 border-2 m-2 rounded-2xl text-xl font-bold text-center"
          :class="friend === 'meraj bhai' ? 'bg-red-500' : 'bg-slate-500'"
        >
          {{ friend }}
        </p>
        <p
          class="absolute top-0 right-0 cursor-pointer bg-red-400 hover:bg-red-600 rounded-full"
          v-on:click="() => deleteName(friend)"
        >
          <CrossIcon />
        </p></div
    ></template>
    <input
      type="text"
      v-model="inputName"
      @keyup.enter="handleClick"
      placeholder="Enter a name"
      class="border-2 p-2"
    />
    <button
      class="p-2 text-lg font-bold bg-green-500 hover:bg-green-400 rounded-2xl mt-4"
      @click="handleClick"
      @keyup.enter="handleClick"
    >
      Add name
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
