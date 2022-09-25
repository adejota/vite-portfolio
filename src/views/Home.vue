<template>
<div class="w-full flex flex-col">
  <header class="w-full px-4 pt-4 mb-4 bg-mid-black rounded-xl border border-extra-low-white overflow-hidden relative">
    <div class="flex pb-4">
      <figure>
        <img src="../assets/images/perfil.jpg" alt="Profile picture"
          class="rounded-3xl mr-4"
          width="80"
        >
      </figure>

      <div>
        <h1 class="text-2xl text-full-white font-bold mb-2">Ademir Jr.</h1>
        <div class="text-sm text-full-white py-1 px-2 bg-low-black rounded-xl">
          <span>Web Developer</span>
        </div>
      </div>

      <button @click="setShowHeaderListItem"
        class="absolute top-0 right-0 p-2"
      >
        <icon
          :name="setChevronIcon"
          :class="'w-6 h-6 text-primary'"
        />
      </button>
    </div>

    <div v-if="showHeaderListItem"
      class="animate__animated animate__fadeIn"
    >
      <div class="flex pt-4 border-b border-t border-extra-low-white">
        <ul>
          <li v-for="headerListItem in headerListItems" :key="headerListItem.title"
            class="flex mb-4"
          >
            <div class="w-8 h-8 mr-2 flex justify-center items-center shadow-full-black shadow rounded-lg">
              <icon
                :name="headerListItem.icon"
                :class="'w-4 h-4 text-primary'"
              />
            </div>

            <div>
              <p class="text-xs text-mid-white uppercase">{{ headerListItem.title }}</p>
              <p class="text-sm text-full-white font-bold">{{ headerListItem.content }}</p>
            </div>
          </li>
        </ul>
      </div>

      <ul class="flex pb-4">
        <li v-for="headerNavListItem in headerNavListItems" :key="headerNavListItem.title"
          class="pt-4 mr-2"        
        >
          <a :href="headerNavListItem.link" target="_blank">
            <icon
              :name="headerNavListItem.icon"
              :class="'w-5 h-5 text-mid-white'"
            />
          </a>
        </li>
      </ul>
    </div>
  </header>

  <section v-if="selectedNavBarItem === 1"
    class="w-full p-4 mb-4 bg-mid-black rounded-xl border border-extra-low-white overflow-hidden animate__animated animate__fadeIn"
  >
    <h2 class="text-2xl text-full-white font-bold">About Me</h2>
    <div class="mt-2 mb-4 w-12 border-2 rounded-xl border-primary"></div>
    <p class="text-mid-white mb-2">Sou graduado em contabilidade desde 2018 e trabalho na área de tecnologia desde 2020.</p>
    <p class="text-mid-white mb-2">Realizei um curso técnico de multimídia integrado ao ensino médio onde aprimorei o meu lado criativo e adquiri habilidades de UX e UI.</p>
    <p class="text-mid-white mb-2">Durante a faculdade e meus primeiros empregos trabalhei bastante o meu lado de negócios, conhecimento que considero crucial para entender mais a fundo a solução que as empresas oferecem.</p>
    <p class="text-mid-white">Atualmente estou atuando como desenvolvedor frontend na Znap Technologies, estudando testes unitários, e2e e aprimorando meus conhecimentos no framework Vue.</p>
  </section>

  <section v-if="selectedNavBarItem === 2"
    class="w-full p-4 mb-4 bg-mid-black rounded-xl border border-extra-low-white overflow-hidden animate__animated animate__fadeIn"
  >
    <h2 class="text-2xl text-full-white font-bold">Resume</h2>
  </section>

  <section v-if="selectedNavBarItem === 3"
    class="w-full p-4 mb-4 bg-mid-black rounded-xl border border-extra-low-white overflow-hidden animate__animated animate__fadeIn"
  >
    <h2 class="text-2xl text-full-white font-bold">Portfolio</h2>
  </section>

  <nav class="absolute bottom-0 left-0 right-0 p-4 bg-mid-black rounded-t-xl overflow-hidden">
    <ul class="flex justify-evenly">
      <li v-for="navBarItem in navBarItems" :key="navBarItem.title"
        class="text-full-white"
      >
        <button @click="selectedNavBarItem = navBarItem.id">
          {{ navBarItem.title }}
        </button>
      </li>
    </ul>
  </nav>
</div>
</template>

<script>
import Icon from '../components/Icon/index.vue'

export default {
  name: 'Home',

  components: { Icon },

  computed: {
    setChevronIcon() {
      return this.showHeaderListItem ? 'ChevronUp' : 'ChevronDown'
    }
  },

  data() {
    return {
      showHeaderListItem: false,
      selectedNavBarItem: 1,
      headerListItems: [
        { title: 'email', content: 'ademir.diamentejunior@gmail.com', icon: 'Mail' },
        { title: 'phone', content: '+5511983506490', icon: 'DevicePhoneMobile' },
        { title: 'location', content: 'São Paulo, Brazil', icon: 'Location'},
        { title: 'birth', content: '01/19/1994', icon: 'Cake' },
      ],

      headerNavListItems: [
        { title: 'linkedin', link: 'https://www.linkedin.com/in/ademir-diamente-jr/', icon: 'Linkedin' },
        { title: 'instagram', link: 'https://www.instagram.com/ade_jota/', icon: 'Instagram' },
        { title: 'twitter', link: 'https://twitter.com/AdemirDiamente', icon: 'Twitter' },
        { title: 'github', link: 'https://github.com/adejota', icon: 'GitHub' },
      ],

      navBarItems: [
        { id: 1, title: 'About' },
        { id: 2, title: 'Resume' },
        { id: 3, title: 'Portfolio' }
      ],
    }
  },

  methods: {
    setShowHeaderListItem() {
      this.showHeaderListItem = !this.showHeaderListItem
    }
  }
}
</script>
