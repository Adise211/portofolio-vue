<template>
  <v-container fluid :style="{ height: containerHeight }">
    <v-row class="align-center justify-center fill-height">
      <template v-for="(group, i) in skillGroups" :key="i">
        <v-col cols="12" md="4">
          <v-hover v-slot="{ isHovering, props }">
            <v-card
              :elevation="isHovering ? 12 : 5"
              v-bind="props"
              class="bg-grey-lighten-3"
              :min-height="isMobile ? '50vh' : ''"
              :max-height="isMobile ? '70vh' : ''"
            >
              <v-card-title class="text-center">
                {{ group.groupTitle }}
              </v-card-title>
              <v-card-text style="height: 60vh">
                <v-list class="bg-grey-lighten-3">
                  <template v-for="(skill, index) in group.items" :key="index">
                    <v-list-item :title="skill.name" class="mt-1">
                      <template v-slot:subtitle>
                        <v-progress-linear
                          v-model="skill.value"
                          color="#9acd32"
                          height="15"
                          rounded
                        >
                          <template v-slot:default="{ value }">
                            <strong>{{ Math.ceil(value) }}%</strong>
                          </template>
                        </v-progress-linear>
                      </template>
                    </v-list-item>
                  </template>
                </v-list>
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
  props: {
    isMobile: {
      type: Boolean,
      default: false,
    },
  },
  data: () => ({}),
  created() {},
  mounted() {},
  methods: {},
  computed: {
    skillGroups() {
      return [
        {
          groupTitle: 'Frontend',
          items: [
            { name: 'HTML/CSS', value: '95%' },
            { name: 'Javascript', value: '95%' },
            { name: 'Vue.js', value: '98%' },
            { name: 'React.js', value: '85%' },
            { name: 'Vuetify', value: '95%' },
            { name: 'Bootstrap', value: '75%' },
          ],
        },
        {
          groupTitle: 'Backend',

          items: [
            { name: 'Node.js', value: '80%' },
            { name: 'Express', value: '75%' },
            { name: 'PostgreSQL', value: '80%' },
            { name: 'Axios', value: '90%' },
            { name: 'SQL', value: '98%' },
          ],
        },
        {
          groupTitle: 'Tools & Others',
          items: [
            { name: 'Git', value: '95%' },
            { name: 'Github', value: '95%' },
            { name: 'SourceTree', value: '85%' },
            { name: 'Firebase', value: '85%' },
            { name: 'Azure DevOps', value: '89%' },
            { name: 'CI/CD', value: '90%' },
            { name: 'Github', value: '95%' },
          ],
        },
      ]
    },
    containerHeight() {
      return !this.isMobile ? '100vh' : '250vh'
    },
  },
  watch: {},
}
</script>

<style scoped>
.test {
  color: yellowgreen;
}
/* 
.height-for-mobile {
he
}

.height-for-desktop {

} */
</style>
