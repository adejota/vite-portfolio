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
        <p class="text-mid-white mb-2">Me formei em contabilidade pela USP em 2018 e estou na área de tecnologia desde 2020.</p>
        <p class="text-mid-white mb-6">Atualmente estou atuando como desenvolvedor web na Znap Technologies, estudando testes automatizados e aprimorando meus conhecimentos no framework Vue.</p>

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
            <p class="text-primary font-bold text-sm">{{ educationListItem.subtitle }}</p>
            <p class="text-mid-white">{{ educationListItem.content }}</p>
          </li>
        </ul>

        <h3 class="text-lg text-full-white font-bold mb-4">Experiência profissional</h3>
        <ul class="text-full-white marker:text-primary list-outside list-disc ml-6 mb-4">
          <li v-for="experienceListItem in experienceListItems" :key="experienceListItem.title"
            class="pb-4"
          >
            <h4 class="font-bold">{{ experienceListItem.title }}</h4>
            <p class="text-primary font-bold text-sm">{{ experienceListItem.subtitle }}</p>
            <p class="text-mid-white">{{ experienceListItem.content }}</p>
          </li>
        </ul>

        <h3 class="text-lg text-full-white font-bold mb-4">Tecnologias</h3>
        <h2 class="text-full-white font-bold mb-4">Linguagens</h2>
        <div class="w-full p-4 mb-8 grid grid-cols-2 gap-2 md:gap-4 md:grid-cols-4 lg:grid-cols-6 border border-extra-low-white shadow-lg shadow-full-black rounded-lg">
          <div v-for="skillsListItem in languageSkillsListItems" :key="skillsListItem.title"
            class="mr-2 p-2 pt-4 flex flex-col justify-center items-center border border-extra-low-white shadow-lg shadow-full-black rounded-lg"
          >
            <icon
              :name="skillsListItem.icon"
              :class="'w-12 h-12'"
            />
            <p class="m-0 mt-2 text-mid-white">{{ skillsListItem.title }}</p>
          </div>
        </div>

        <h2 class="text-full-white font-bold mb-4">Backend e banco de dados</h2>
        <div class="w-full p-4 mb-8 grid grid-cols-2 gap-2 md:gap-4 md:grid-cols-4 lg:grid-cols-6 border border-extra-low-white shadow-lg shadow-full-black rounded-lg">
          <div v-for="skillsListItem in backendSkillsListItems" :key="skillsListItem.title"
            class="mr-2 p-2 pt-4 flex flex-col justify-center items-center border border-extra-low-white shadow-lg shadow-full-black rounded-lg"
          >
            <icon
              :name="skillsListItem.icon"
              :class="'w-12 h-12'"
            />
            <p class="m-0 mt-2 text-mid-white">{{ skillsListItem.title }}</p>
          </div>
        </div>

        <h2 class="text-full-white font-bold mb-4">Frontend e design</h2>
        <div class="w-full p-4 mb-8 grid grid-cols-2 gap-2 md:gap-4 md:grid-cols-4 lg:grid-cols-6 border border-extra-low-white shadow-lg shadow-full-black rounded-lg">
          <div v-for="skillsListItem in frontendSkillsListItems" :key="skillsListItem.title"
            class="mr-2 p-2 pt-4 flex flex-col justify-center items-center border border-extra-low-white shadow-lg shadow-full-black rounded-lg"
          >
            <icon
              :name="skillsListItem.icon"
              :class="'w-12 h-12'"
            />
            <p class="m-0 mt-2 text-mid-white">{{ skillsListItem.title }}</p>
          </div>
        </div>

        <h2 class="text-full-white font-bold mb-4">Testes automatizados</h2>
        <div class="w-full p-4 mb-8 grid grid-cols-2 gap-2 md:gap-4 md:grid-cols-4 lg:grid-cols-6 border border-extra-low-white shadow-lg shadow-full-black rounded-lg">
          <div v-for="skillsListItem in testsSkillsListItems" :key="skillsListItem.title"
            class="mr-2 p-2 pt-4 flex flex-col justify-center items-center border border-extra-low-white shadow-lg shadow-full-black rounded-lg"
          >
            <icon
              :name="skillsListItem.icon"
              :class="'w-12 h-12'"
            />
            <p class="m-0 mt-2 text-mid-white">{{ skillsListItem.title }}</p>
          </div>
        </div>

        <h2 class="text-full-white font-bold mb-4">Versionamento</h2>
        <div class="w-full p-4 mb-8 grid grid-cols-2 gap-2 md:gap-4 md:grid-cols-4 lg:grid-cols-6 border border-extra-low-white shadow-lg shadow-full-black rounded-lg">
          <div v-for="skillsListItem in versioningSkillsListItems" :key="skillsListItem.title"
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

        <div class="grid grid-cols-1 lg:grid-cols-2 gap-4">
          <div v-for="portfolioListItem in portfolioListItems" :key="portfolioListItem.name"
            class="animate__animated animate__zoomIn animate__faster w-full h-full flex flex-col justify-between"
          >
            <div>
              <a :href="portfolioListItem.link" target="_blank">
                <img :src="getImageUrl(portfolioListItem.name)" :alt="`${portfolioListItem.name} project cover`"
                  class="rounded-xl"
                >
              </a>
              <h3 class="mt-2 text-full-white font-bold">{{ portfolioListItem.title }}</h3>
              <p class="text-sm text-mid-white mb-2">{{ portfolioListItem.content }}</p>
            </div>
            <div class="flex justify-end">
              <a :href="portfolioListItem.repo" target="_blank">
                <icon
                  :name="'GitHub'"
                  :class="'w-6 h-6 text-mid-white hover:text-white transition-colors'"
                />
              </a>
            </div>
          </div>
        </div>
      </div>

      <nav class="p-4 bg-mid-black rounded-t-xl overflow-hidden backdrop-blur-lg bg-opacity-20 z-10
        fixed bottom-0 left-0 right-0 
        xl:absolute xl:top-0 xl:right-0 xl:left-1/2 xl:bottom-auto xl:bg-low-black xl:rounded-none xl:rounded-bl-xl xl:border xl:border-extra-low-white
        overflow-visible"
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

          <div class="relative">
            <button @click="showLanguageDialog = !showLanguageDialog">
              <icon
                name="Language"
                :class="'w-6 h-6 text-full-white'"
              />
            </button>

            <div v-if="showLanguageDialog"
              class="absolute -top-36 -right-5 xl:top-9 z-20"
            >
              <div class="py-7 px-5 xl:p-4 border border-extra-low-white bg-mid-black rounded shadow-xl">
                <ul>
                  <li v-for="(language, index) in languages"
                    class="cursor-pointer"
                    :class="{'mt-4': index !== 0}"
                    @click="setLanguage(language)"
                  >
                    <span :class="language.code === selectedLanguage ? 'text-primary' : 'text-white'">{{ language.name }}</span>
                  </li>
                </ul>
              </div>
            </div>
          </div>
        </div>
      </nav>
    </section>
  </div>
</template>

<script>
import Icon from '../components/Icon/index.vue'
import getData from '../data'

export default {
  name: 'Home',

  components: { Icon },

  computed: {
    setChevronIcon() {
      return this.showHeaderListItem ? 'ChevronUp' : 'ChevronDown'
    },

    languageSkillsListItems() {
      return this.skillsListItems.length ? this.skillsListItems.filter(i => i.category === 'language') : []
    },

    backendSkillsListItems() {
      return this.skillsListItems.length ? this.skillsListItems.filter(i => i.category === 'backend') : []
    },

    frontendSkillsListItems() {
      return this.skillsListItems.length ? this.skillsListItems.filter(i => i.category === 'frontend') : []
    },

    testsSkillsListItems() {
      return this.skillsListItems.length ? this.skillsListItems.filter(i => i.category === 'tests') : []
    },

    versioningSkillsListItems() {
      return this.skillsListItems.length ? this.skillsListItems.filter(i => i.category === 'versioning') : []
    },
  },

  created() {
    const {
      languages,
      headerListItems,
      headerNavListItems,
      aboutListItems,
      doingListItems,
      educationListItems,
      experienceListItems,
      skillsListItems,
      portfolioListItems,
      navBarItems
    } = getData(this.selectedLanguage)

    this.languages = languages
    this.headerListItems = headerListItems
    this.headerNavListItems = headerNavListItems
    this.aboutListItems = aboutListItems
    this.doingListItems = doingListItems
    this.educationListItems = educationListItems
    this.experienceListItems = experienceListItems
    this.skillsListItems = skillsListItems
    this.portfolioListItems = portfolioListItems
    this.navBarItems = navBarItems
  },

  data() {
    return {
      showLanguageDialog: false,
      selectedLanguage: 'pt-BR',
      languages: [],
      width: null,
      height: null,
      showHeaderListItem: false,
      selectedNavBarItem: 1,
      headerListItems: [],
      headerNavListItems: [],
      aboutListItems: [],
      doingListItems: [],
      educationListItems: [],
      experienceListItems: [],
      skillsListItems: [],
      portfolioListItems: [],
      navBarItems: [],
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

      if (item.content === 'Projetos') {
        return this.portfolioListItems.length
      }

      return item.title
    },

    setLanguage(language) {
      this.selectedLanguage = language.code
      this.showLanguageDialog = false
    },

    calcTime(since) {
      let sinceTime = new Date(since).getTime()
      let ageDifMs = Date.now() - sinceTime
      let ageDate = new Date(ageDifMs)

      let year = ageDate.getUTCFullYear() - 1970
      let month = ageDate.getMonth()
      let total = parseFloat((year * 12 + month) / 12).toFixed(1)

      let text = this.selectedLanguage === 'pt-BR' ? total.toString().replace('.', ',') : total.toString()
      
      return `+ ${text}`
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

