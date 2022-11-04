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
import JsLogo from './JsLogo.vue'
import NodeLogo from './NodeLogo.vue'
import VueLogo from './VueLogo.vue'
import HtmlLogo from './HtmlLogo.vue'
import CssLogo from './CssLogo.vue'
import TailwindLogo from './TailwindLogo.vue'
import VuetifyLogo from './VuetifyLogo.vue'
import FigmaLogo from './FigmaLogo.vue'
import GithubLogo from './GithubLogo.vue'
import JestLogo from './JestLogo.vue'
import CypressLogo from './CypressLogo.vue'
import MysqlLogo from './MysqlLogo.vue'
import PostgreLogo from './PostgreLogo.vue'
import OfficeLogo from './OfficeLogo.vue'
import ExcelLogo from './ExcelLogo.vue'

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
    JsLogo,
    NodeLogo,
    VueLogo,
    HtmlLogo,
    CssLogo,
    TailwindLogo,
    VuetifyLogo,
    FigmaLogo,
    GithubLogo,
    JestLogo,
    CypressLogo,
    MysqlLogo,
    PostgreLogo,
    OfficeLogo,
    ExcelLogo,
  },

  props: {
    name: { type: String, required: true }
  }
}
</script>
