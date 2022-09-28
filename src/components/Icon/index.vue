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
import Briefcase from './Briefcase.vue'
import LightBulb from './LightBulb.vue'
import AcademicCap from './AcademicCap.vue'
import CodeBracketSquare from './CodeBracketSquare.vue'
import PencilSquare from './PencilSquare.vue'
import Language from './Language.vue'
import UserGroup from './UserGroup.vue'

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
    ChevronUp,
    Briefcase,
    LightBulb,
    AcademicCap,
    CodeBracketSquare,
    PencilSquare,
    Language,
    UserGroup,
  },

  props: {
    name: { type: String, required: true }
  }
}
</script>
