<template>
  <v-container fluid class="fill-height">
    <v-row v-if="isMobile" class="page-title text-h4 mb-15 mt-2">
      <span class="mx-auto">Projects</span>
    </v-row>
    <v-row class="align-center justify-center fill-height">
      <template v-for="(item, i) in projects" :key="i">
        <v-col cols="12" md="6">
          <!-- <v-hover v-slot="{ isHovering, props }"> -->
          <v-card
            :class="{ 'bg-grey-lighten-3': isDarkMode }"
            :elevation="5"
            :max-height="isMobile ? '140vh' : ''"
            :min-height="isMobile ? '110vh' : ''"
            v-bind="props"
          >
            <v-img :src="item.img" height="250px" max-height="250px" cover> </v-img>
            <v-card-text style="height: 50vh; max-height: 50vh">
              <div class="project-title mb-5">
                <p class="text-h6">{{ item.title }}</p>
                <p class="text-body-1 font-weight-bold">{{ item.text }}</p>
              </div>
              <div class="project-desc text-subtitle-1">{{ item.description }}</div>
              <div class="project-tools d-flex flex-row flex-wrap mt-5">
                <v-chip
                  v-for="(tool, index) in item.tools"
                  :key="index"
                  color="light-green"
                  variant="outlined"
                  class="mx-2 mt-3"
                >
                  {{ tool }}
                </v-chip>
              </div>
              <div class="project-sources position-absolute right-0 bottom-0 text-end mb-4 mr-4">
                <v-icon @click="goToProjectSource(item.sources.github)">mdi-github</v-icon>
                <v-icon @click="goToProjectSource(item.sources.web)">mdi-web</v-icon>
              </div>
            </v-card-text>
          </v-card>
          <!-- </v-hover> -->
        </v-col>
      </template>
    </v-row>
  </v-container>
</template>

<script>
export default {
  components: {},
  props: {
    isDarkMode: {
      type: Boolean,
      default: false,
    },
    isMobile: {
      type: Boolean,
      default: false,
    },
  },
  data: () => ({}),
  created() {},
  mounted() {},
  methods: {
    goToProjectSource(source) {
      window.open(source)
    },
  },
  computed: {
    projects() {
      return [
        {
          title: 'Customer Relationship Management Platform',
          text: `SalesPro`,
          description:
            'A serverless CRM platform aimed at helping businesses manage customer data and sales. Inspired by Salesforce, the app is built with Vue 3 and utilizes Vuetify for UI components and Firebase for authentication, database and hosting.',
          img: 'images/sales_pro_project.png',
          tools: ['Vue', 'Vuetify', 'Firebase', 'Github', 'SASS', 'Azure DevOps (CI/CD)', 'Git'],
          sources: {
            github: 'https://github.com/Adise211/salesPro',
            web: 'https://salespro-45922.web.app/',
          },
        },
        {
          title: 'Coming Soon!',
          text: `Stay tuned...`,
          description:
            'Lorem ipsum, dolor sit amet consectetur adipisicing elit. Ad commodi blanditiis dolor praesentium incidunt expedita nulla officia quibusdam, dolorum alias? Corporis voluptatem modi expedita iusto quos molestiae dolores ex libero.',
          img: 'https://cdn.vuetifyjs.com/docs/images/cards/hands.jpg',
          tools: ['Javascript'],
        },
      ]
    },
    transparentColor() {
      return 'rgba(255, 255, 255, 0)'
    },
  },
  watch: {},
}
</script>

<style scoped>
/* .v-card {
  transition: opacity 0.4s ease-in-out;
}

.v-card:not(.on-hover) {
  opacity: 0.8;
} */

.show-btns {
  color: rgba(255, 255, 255, 1) !important;
}
</style>
