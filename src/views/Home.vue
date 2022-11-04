<template>
  <div class="flex flex-col xl:flex-row xl:justify-between p-4 xl:p-16">
    <header class="w-full xl:max-w-md xl:mr-8 xl:h-full px-4 pt-4 mb-4  bg-mid-black rounded-xl border border-extra-low-white overflow-hidden relative">
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
            <span>Desenvolvedor web</span>
          </div>
        </div>

        <button @click="setShowHeaderListItem"
          class="absolute top-0 right-0 p-2 xl:hidden"
        >
          <icon
            :name="setChevronIcon"
            :class="'w-6 h-6 text-primary'"
          />
        </button>
      </div>

      <div v-if="showHeaderListItem || width >= 1440"
        class="animate__animated animate__fadeIn"
      >
        <div class="flex pt-4 border-b border-t border-extra-low-white">
          <ul>
            <li v-for="headerListItem in headerListItems" :key="headerListItem.title"
              class="flex mb-4"
            >
              <div class="w-8 h-8 mr-2 flex justify-center items-center border border-extra-low-white shadow-lg shadow-full-black rounded-lg">
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

    <section class="relative w-full p-4 mb-14 lg:mb-4 xl:mb-0 bg-mid-black rounded-xl border border-extra-low-white overflow-hidden">
      <div v-if="selectedNavBarItem === 1" class="animate__animated animate__fadeIn">
        <h2 class="text-2xl text-full-white font-bold">Sobre mim</h2>
        <div class="mt-2 mb-6 w-12 border-2 rounded-xl border-primary bg-primary"></div>
        <p class="text-mid-white mb-2">Sou graduado em contabilidade desde 2018 e trabalho na área de tecnologia desde 2020.</p>
        <p class="text-mid-white mb-2">Realizei um curso técnico de multimídia integrado ao ensino médio onde aprimorei o meu lado criativo e adquiri habilidades de UX e UI.</p>
        <p class="text-mid-white mb-2">Durante a faculdade e meus primeiros empregos trabalhei bastante o meu lado de negócios, conhecimento que considero crucial para entender mais a fundo a solução que as empresas oferecem.</p>
        <p class="text-mid-white mb-6">Atualmente estou atuando como desenvolvedor frontend na Znap Technologies, estudando testes unitários, e2e e aprimorando meus conhecimentos no framework Vue.</p>

        <div class="grid grid-cols-2 lg:grid-cols-2 gap-4 mt-4 mb-8">
          <div v-for="aboutListItem in aboutListItems" :key="aboutListItem.title"
            class="flex flex-col items-center w-full h-full p-4 border border-extra-low-white shadow-lg rounded-xl shadow-full-black"
            style="min-height: 150px;"
          >
            <icon
              :name="aboutListItem.icon"
              :class="'w-8 h-8 text-primary mb-2'"
            />
            <h4 class="text-2xl text-full-white font-bold">{{ setAboutListItemTitle(aboutListItem) }}</h4>
            <p class="text-sm text-mid-white text-center mt-1">{{ aboutListItem.content }}</p>
          </div>
        </div>

        <h3 class="text-lg text-full-white font-bold">O que estou fazendo</h3>

        <div class="grid grid-cols-1 lg:grid-cols-2 gap-4 mt-4 mb-8">
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
      </div>

      <div v-if="selectedNavBarItem === 2" class="animate__animated animate__fadeIn">
        <h2 class="text-2xl text-full-white font-bold">Currículo</h2>
        <div class="mt-2 mb-6 w-12 border-2 rounded-xl border-primary bg-primary"></div>

        <h3 class="text-lg text-full-white font-bold mb-4">Escolaridade</h3>
        <ul class="text-full-white marker:text-primary list-outside list-disc ml-6 mb-4">
          <li v-for="educationListItem in educationListItems" :key="educationListItem.title"
            class="pb-4"
          >
            <h4 class="font-bold">{{ educationListItem.title }}</h4>
            <p class="text-primary font-bold">{{ educationListItem.subtitle }}</p>
            <p class="text-mid-white">{{ educationListItem.content }}</p>
          </li>
        </ul>

        <h3 class="text-lg text-full-white font-bold mb-4">Experiência profissional</h3>
        <ul class="text-full-white marker:text-primary list-outside list-disc ml-6 mb-4">
          <li v-for="experienceListItem in experienceListItems" :key="experienceListItem.title"
            class="pb-4"
          >
            <h4 class="font-bold">{{ experienceListItem.title }}</h4>
            <p class="text-primary font-bold">{{ experienceListItem.subtitle }}</p>
            <p class="text-mid-white">{{ experienceListItem.content }}</p>
          </li>
        </ul>

        <h3 class="text-lg text-full-white font-bold mb-4">Tecnologias</h3>
        <div class="w-full p-4 mb-8 grid grid-cols-2 gap-2 md:gap-4 md:grid-cols-4 lg:grid-cols-6 border border-extra-low-white shadow-lg shadow-full-black rounded-lg">
          <div v-for="skillsListItem in skillsListItems" :key="skillsListItem.title"
            class="mr-2 p-2 pt-4 flex flex-col justify-center items-center border border-extra-low-white shadow-lg shadow-full-black rounded-lg"
          >
            <icon
              :name="skillsListItem.icon"
              :class="'w-12 h-12'"
            />
            <p class="m-0 mt-2 text-mid-white">{{ skillsListItem.title }}</p>
          </div>
        </div>
      </div>

      <div v-if="selectedNavBarItem === 3" class="animate__animated animate__fadeIn">
        <h2 class="text-2xl text-full-white font-bold">Portfolio</h2>
        <div class="mt-2 mb-6 w-12 border-2 rounded-xl border-primary bg-primary"></div>

        <div class="grid grid-cols-1 lg:grid-cols-2 lg:gap-4">
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
        </div>
      </div>

      <nav class="p-4 bg-mid-black rounded-t-xl overflow-hidden backdrop-blur-lg bg-opacity-20 z-10
        fixed bottom-0 left-0 right-0 
        xl:absolute xl:top-0 xl:right-0 xl:left-1/2 xl:bottom-auto xl:bg-low-black xl:rounded-none xl:rounded-bl-xl xl:border xl:border-extra-low-white"
      >
        <div class="flex justify-evenly">
          <ul class="flex justify-evenly w-10/12">
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

          <button>
            <icon
              name="Language"
              :class="'w-6 h-6 text-full-white'"
            />
          </button>
        </div>
      </nav>
    </section>
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
    },
  },

  data() {
    return {
      width: null,
      height: null,
      showHeaderListItem: false,
      selectedNavBarItem: 1,
      headerListItems: [
        { title: 'email', content: 'ademir.diamentejunior@gmail.com', icon: 'Mail' },
        { title: 'celular', content: '+5511983506490', icon: 'DevicePhoneMobile' },
        { title: 'localização', content: 'São Paulo, Brazil', icon: 'Location' },
        { title: 'nascimento', content: '01/19/1994', icon: 'Cake' },
      ],

      headerNavListItems: [
        { title: 'linkedin', link: 'https://www.linkedin.com/in/ademir-diamente-jr/', icon: 'Linkedin' },
        { title: 'instagram', link: 'https://www.instagram.com/ade_jota/', icon: 'Instagram' },
        { title: 'twitter', link: 'https://twitter.com/AdemirDiamente', icon: 'Twitter' },
        { title: 'github', link: 'https://github.com/adejota', icon: 'GitHub' },
      ],

      aboutListItems: [
        { title: '+2', content: 'Anos de experiência com tecnologia', icon: 'Briefcase', since: '03/01/2020' },
        { title: '+10', content: 'Projetos completados', icon: 'LightBulb' },
        // { title: '+10', content: 'Training & courses', icon: 'AcademicCap' },
      ],

      doingListItems: [
        { title: 'Desenvolvimento Web', content: 'Desenvolvimento de sites de alta qualidade a nível profissional', icon: 'CodeBracketSquare' },
        { title: 'Git flow', content: 'Controle do versionamento do código e deploy do sistema', icon: 'GitHub' },
        { title: 'Gestão de pessoas ', content: 'Responsável pelo code-review, atribuição de tarefas e prazos', icon: 'UserGroup' },
      ],

      educationListItems: [
        { title: 'Universidade de São Paulo', subtitle: '2013 — 2018', content: 'Bacharelado, Ciências contábeis'},
        { title: 'Université Paris Dauphine', subtitle: '2016 — 2016', content: 'Intercâmbio, Negócios'},
      ],

      experienceListItems: [
        { title: 'Desenvolvedor web', subtitle: 'Znap Technologies | mar 2021 — atualmente', content: 'Atuo com foco no front-end em um sistema Vue.js modularizado em diferentes SPAs. Sou responsável por desenvolver componentes genéricos que seguem o princípio de low-coding e são utilizados em todas as views do sistema. Contribuo com code-review dos meus pares, além de ser o responsável por controlar o versionamento do código e o deploy do sistema' },
        { title: 'Product Owner', subtitle: 'Lavapp | mar 2020 — mar 2021', content: 'Atuei como PO em uma webview com front-end em Vue.js e API Laravel. Também fui responsável por elaborar relatórios gerenciais com objetivo de criar e analisar indicadores estratégicos para a área comercial e financeira' },
        { title: 'Analista', subtitle: 'Petroplus | fev 2018 — fev 2020', content: 'Atuei auxiliando decisões de nível gerencial com foco na melhoria de processos e planejamento estratégico' },
        { title: 'Estagiário comercial', subtitle: 'Petroplus | mar 2017 — jan 2018', content: '' },
        { title: 'Estagiário de contabilidade', subtitle: 'Banco Safra | out 2015 — jul 2016', content: '' },
      ],

      skillsListItems: [
        { title: 'Javascript', icon: 'JsLogo' },
        { title: 'HTML', icon: 'HtmlLogo' },
        { title: 'CSS', icon: 'CssLogo' },
        { title: 'Vue', icon: 'VueLogo' },
        { title: 'Tailwind', icon: 'TailwindLogo' },
        { title: 'Vuetify', icon: 'VuetifyLogo' },
        { title: 'Figma', icon: 'FigmaLogo' },
        { title: 'GitHub', icon: 'GithubLogo' },
        { title: 'Jest', icon: 'JestLogo' },
        { title: 'Cypress', icon: 'CypressLogo' },
        { title: 'Node', icon: 'NodeLogo' },
        { title: 'MySQL', icon: 'MysqlLogo' },
        { title: 'PostgreSQL', icon: 'PostgreLogo' },
        { title: 'Office', icon: 'OfficeLogo' },
        { title: 'Excel', icon: 'ExcelLogo' },
      ],

      portfolioListItems: [
        { name: 'le-tip', title: 'Le/Tip', content: 'Web app description', link: 'https://adejota-le-tip.netlify.app/' },
        { name: 'memory-game', title: 'Memory game', content: 'Web app description', link: 'https://adejota-memory-game.netlify.app/' }
      ],

      navBarItems: [
        { id: 1, title: 'Sobre' },
        { id: 2, title: 'Currículo' },
        { id: 3, title: 'Portfolio' }
      ],
    }
  },

  mounted() {
    this.getWindowSize()
    window.addEventListener('resize', this.getWindowSize);
  },

  unmounted() {
    window.removeEventListener('resize', this.getWindowSize);
  },

  methods: {
    getWindowSize() {
      this.width = document.documentElement.clientWidth;
      this.height = document.documentElement.clientHeight;
    },

    setShowHeaderListItem() {
      return this.showHeaderListItem = !this.showHeaderListItem
    },

    setAboutListItemTitle(item) {
      if (item.content === 'Anos de experiência com tecnologia') {
        return this.calcTime(item.since)
      }

      if (item.content === 'Projetos completados') {
        return this.portfolioListItems.length
      }

      return item.title
    },

    calcTime(since) {
      let sinceTime = new Date(since).getTime()
      let ageDifMs = Date.now() - sinceTime
      let ageDate = new Date(ageDifMs)

      let year = ageDate.getUTCFullYear() - 1970
      let month = ageDate.getMonth()
      let total = parseFloat((year * 12 + month) / 12).toFixed(1)
      
      return `+ ${total}`
    },

    getImageUrl(name) {
      return new URL(`../assets/images/${name}.png`, import.meta.url).href
    },
  }
}
</script>

<style>

.test {
  color: #4e83f5
}
</style>

