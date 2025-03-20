<template>
  <v-container fluid style="height: 100vh">
    <v-row class="align-center justify-center fill-height">
      <template v-for="(item, i) in projects" :key="i">
        <v-col cols="12" md="6">
          <v-hover v-slot="{ isHovering, props }">
            <v-card
              :class="{ 'on-hover': isHovering }"
              :elevation="isHovering ? 12 : 2"
              v-bind="props"
            >
              <v-img :src="item.img" height="250px" max-height="250px" cover>
                <!-- <v-card-title class="text-h6 text-black d-flex flex-column">
                  <p class="mt-4">
                    {{ item.title }}
                  </p>

                  <div>
                    <p class="ma-0 text-body-1 font-weight-bold">
                      {{ item.text }}
                    </p>
                    <p class="text-caption font-weight-medium">
                      {{ item.subtext }}
                    </p>
                  </div>
                </v-card-title> -->
              </v-img>
              <v-card-text>
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
                <div class="project-sources text-end">
                  <v-icon @click="goToProjectSource(item.sources.github)">mdi-github</v-icon>
                  <v-icon @click="goToProjectSource(item.sources.web)">mdi-web</v-icon>
                </div>
              </v-card-text>
            </v-card>
          </v-hover>
        </v-col>
      </template>
    </v-row>
  </v-container>
</template>

<script>
export default {
  components: {},
  props: {},
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
          title: 'Manage Customers CRM Platform',
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
          title: 'Comming Soon!',
          text: `Stay tuned...`,
          img: 'https://cdn.vuetifyjs.com/docs/images/cards/hands.jpg',
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
.v-card {
  transition: opacity 0.4s ease-in-out;
}

.v-card:not(.on-hover) {
  opacity: 0.8;
}

.show-btns {
  color: rgba(255, 255, 255, 1) !important;
}
</style>
