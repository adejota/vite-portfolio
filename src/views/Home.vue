<template>
  <div class="flex flex-col p-4">
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
      class="w-full p-4 mb-14 bg-mid-black rounded-xl border border-extra-low-white overflow-hidden animate__animated animate__fadeIn"
    >
      <h2 class="text-2xl text-full-white font-bold">About Me</h2>
      <div class="mt-2 mb-6 w-12 border-2 rounded-xl border-primary bg-primary"></div>
      <p class="text-mid-white mb-2">Sou graduado em contabilidade desde 2018 e trabalho na área de tecnologia desde 2020.</p>
      <p class="text-mid-white mb-2">Realizei um curso técnico de multimídia integrado ao ensino médio onde aprimorei o meu lado criativo e adquiri habilidades de UX e UI.</p>
      <p class="text-mid-white mb-2">Durante a faculdade e meus primeiros empregos trabalhei bastante o meu lado de negócios, conhecimento que considero crucial para entender mais a fundo a solução que as empresas oferecem.</p>
      <p class="text-mid-white mb-6">Atualmente estou atuando como desenvolvedor frontend na Znap Technologies, estudando testes unitários, e2e e aprimorando meus conhecimentos no framework Vue.</p>

      <div class="grid grid-cols-2 gap-4 mt-4 mb-8">
        <div v-for="aboutListItem in aboutListItems" :key="aboutListItem.title"
          class="flex flex-col items-center w-full p-4 border border-extra-low-white shadow-lg rounded-xl shadow-full-black"
        >
          <icon
            :name="aboutListItem.icon"
            :class="'w-8 h-8 text-primary mb-2'"
          />
          <h4 class="text-2xl text-full-white font-bold">{{ aboutListItem.title }}</h4>
          <p class="text-sm text-mid-white text-center mt-1">{{ aboutListItem.content }}</p>
        </div>
      </div>

      <h3 class="text-lg text-full-white font-bold">What I'm Doing</h3>

      <div class="grid grid-cols-1 gap-4 mt-4 mb-8">
        <div v-for="doingListItem in doingListItems" :key="doingListItem.title"
          class="flex flex-col items-center w-full p-4 border border-extra-low-white shadow-lg rounded-xl shadow-full-black"
        >
          <icon
            :name="doingListItem.icon"
            :class="'w-8 h-8 text-primary mb-2'"
          />
          <h4 class="text-full-white font-bold">{{ doingListItem.title }}</h4>
          <p class="text-sm text-mid-white text-center mt-1">{{ doingListItem.content }}</p>
        </div>
      </div>
    </section>

    <section v-if="selectedNavBarItem === 2"
      class="w-full p-4 mb-14 bg-mid-black rounded-xl border border-extra-low-white overflow-hidden animate__animated animate__fadeIn"
    >
      <h2 class="text-2xl text-full-white font-bold">Resume</h2>

      <div class="mt-2 mb-6 w-12 border-2 rounded-xl border-primary bg-primary"></div>

      <h3 class="text-lg text-full-white font-bold mb-4">Education</h3>
      <ul class="text-full-white marker:text-primary list-outside list-disc ml-6 mb-4">
        <li v-for="educationListItem in educationListItems" :key="educationListItem.title"
          class="pb-4"
        >
          <h4 class="font-bold">{{ educationListItem.title }}</h4>
          <p class="text-primary font-bold">{{ educationListItem.subtitle }}</p>
          <p class="text-mid-white">{{ educationListItem.content }}</p>
        </li>
      </ul>

      <h3 class="text-lg text-full-white font-bold mb-4">Experience</h3>
      <ul class="text-full-white marker:text-primary list-outside list-disc ml-6 mb-4">
        <li v-for="experienceListItem in experienceListItems" :key="experienceListItem.title"
          class="pb-4"
        >
          <h4 class="font-bold">{{ experienceListItem.title }}</h4>
          <p class="text-primary font-bold">{{ experienceListItem.subtitle }}</p>
          <p class="text-mid-white">{{ experienceListItem.content }}</p>
        </li>
      </ul>

      <h3 class="text-lg text-full-white font-bold mb-4">My skills</h3>
    </section>

    <section v-if="selectedNavBarItem === 3"
      class="w-full p-4 mb-14 bg-mid-black rounded-xl border border-extra-low-white overflow-hidden animate__animated animate__fadeIn"
    >
      <h2 class="text-2xl text-full-white font-bold">Portfolio</h2>
      <div class="mt-2 mb-6 w-12 border-2 rounded-xl border-primary bg-primary"></div>

      <div v-for="portfolioListItem in portfolioListItems" :key="portfolioListItem.name"
        class="animate__animated animate__zoomIn animate__faster"
      >
        <a :href="portfolioListItem.link" target="_blank">
          <img :src="getImageUrl(portfolioListItem.name)" :alt="`${portfolioListItem.name} project cover`"
            class="rounded-xl"
          >
          <h3 class="mt-2 text-full-white font-bold">{{ portfolioListItem.title }}</h3>
          <p class="text-sm text-mid-white mb-8">{{ portfolioListItem.content }}</p>
        </a>
      </div>
    </section>
  </div>

  <nav class="fixed bottom-0 left-0 right-0 p-4 bg-mid-black rounded-t-xl overflow-hidden">
    <ul class="flex justify-evenly">
      <li v-for="navBarItem in navBarItems" :key="navBarItem.title"
        class="text-full-white transition-colors"
        :class="{'font-bold text-primary': selectedNavBarItem === navBarItem.id}"
      >
        <button @click="selectedNavBarItem = navBarItem.id"
          class="focus:outline-none"
        >
          {{ navBarItem.title }}
        </button>
      </li>
    </ul>
  </nav>
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
        { title: 'location', content: 'São Paulo, Brazil', icon: 'Location' },
        { title: 'birth', content: '01/19/1994', icon: 'Cake' },
      ],

      headerNavListItems: [
        { title: 'linkedin', link: 'https://www.linkedin.com/in/ademir-diamente-jr/', icon: 'Linkedin' },
        { title: 'instagram', link: 'https://www.instagram.com/ade_jota/', icon: 'Instagram' },
        { title: 'twitter', link: 'https://twitter.com/AdemirDiamente', icon: 'Twitter' },
        { title: 'github', link: 'https://github.com/adejota', icon: 'GitHub' },
      ],

      aboutListItems: [
        { title: '+2', content: 'Years of experience', icon: 'Briefcase' },
        { title: '+10', content: 'Projects completed', icon: 'LightBulb' },
        { title: '+10', content: 'Training & courses', icon: 'AcademicCap' },
      ],

      doingListItems: [
        { title: 'Web Development', content: 'High-quality development of sites at the professional level', icon: 'CodeBracketSquare' },
        { title: 'Web Design', content: 'The most modern and high-quality design made at a professional level', icon: 'PencilSquare' },
      ],

      educationListItems: [
        { title: 'Universidade de São Paulo', subtitle: '2013 — 2018', content: 'Bachelors, Accounting'},
        { title: 'Université Paris Dauphine', subtitle: '2016 — 2016', content: 'Exchange program, Business'},
      ],

      experienceListItems: [
        { title: 'Frontend Developer', subtitle: 'Znap Technologies | mar 2021 — present', content: 'Atuo com foco no front-end em um sistema Vue.js modularizado em diferentes SPAs. Sou responsável por desenvolver componentes genéricos que seguem o princípio de low-coding e são utilizados em todas as views do sistema. Contribuo com code-review dos meus pares, além de ser o responsável por controlar o versionamento do código e o deploy do sistema' },
        { title: 'Product Owner', subtitle: 'Lavapp | mar 2020 — mar 2021', content: 'Atuei como PO em uma webview com front-end em Vue.js e API Laravel. Também fui responsável por elaborar relatórios gerenciais com objetivo de criar e analisar indicadores estratégicos para a área comercial e financeira' },
        { title: 'Analista', subtitle: 'Petroplus | feb 2018 — feb 2020', content: 'Atuei auxiliando decisões de nível gerencial com foco na melhoria de processos e planejamento estratégico' },
        { title: 'Estagiário comercial', subtitle: 'Petroplus | mar 2017 — jan 2018', content: '' },
        { title: 'Estagiário de contabilidade', subtitle: 'Banco Safra | oct 2015 — jul 2016', content: '' },
      ],

      skillsListItems: [
        { title: 'HTML/CSS', percentage: 95 },
        { title: 'Javascript', percentage: 90 },
        { title: 'Vue.js', percentage: 90 },
        { title: 'Tailwind', percentage: 90 },
        { title: 'Vuetify', percentage: 90 },
        { title: 'GitHub', percentage: 90 },
        { title: 'MySQL', percentage: 90 },
        { title: 'Node.js', percentage: 90 },
      ],

      portfolioListItems: [
        { name: 'le-tip', title: 'Le/Tip', content: 'Web app description', link: 'https://adejota-le-tip.netlify.app/' },
        { name: 'memory-game', title: 'Memory game', content: 'Web app description', link: 'https://adejota-memory-game.netlify.app/' }
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
    },

    getImageUrl(name) {
      return new URL(`../assets/images/${name}.png`, import.meta.url).href
    }
  }
}
</script>
