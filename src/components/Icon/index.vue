<template>
  <component :is="name" v-bind="$props" />
</template>

<script>
import Mail from './Mail.vue'
import DevicePhoneMobile from './DevicePhoneMobile.vue'
import Location from './Location.vue'
import Cake from './Cake.vue'
import Linkedin from './Linkedin.vue'
import Instagram from './Instagram.vue'
import Twitter from './Twitter.vue'
import GitHub from './GitHub.vue'
import ChevronDown from './ChevronDown.vue'
import ChevronUp from './ChevronUp.vue'

export default {
  components: {
    Mail,
    DevicePhoneMobile,
    Location,
    Cake,
    Linkedin,
    Instagram,
    Twitter,
    GitHub,
    ChevronDown,
    ChevronUp
  },

  props: {
    name: { type: String, required: true }
  }
}
</script>
