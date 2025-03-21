<template>
  <v-container fluid class="mb-16">
    <v-timeline class="align-start" truncate-line="end">
      <v-timeline-item v-for="(item, i) in items" :key="i" :dot-color="item.color" fill-dot>
        <v-card elevation="5" :class="{ 'bg-grey-lighten-3': isDarkMode }">
          <v-card-title class="d-flex align-center">
            <span>{{ item.title }}</span>
            <v-spacer></v-spacer>
            <span class="text-subtitle-2">{{ item.from }} - {{ item.to }}</span>
          </v-card-title>
          <v-card-subtitle>{{ item.subtitle }}</v-card-subtitle>
          <v-card-text>
            <v-list
              v-for="(desc, index) in item.description"
              :key="index"
              :class="{ 'bg-grey-lighten-3': isDarkMode }"
            >
              <v-list-item>* {{ desc.point }}</v-list-item>
            </v-list>
          </v-card-text>
        </v-card>
      </v-timeline-item>
    </v-timeline>
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
  methods: {},
  computed: {
    items() {
      return [
        {
          title: 'Frontend Developer',
          subtitle: 'Wyze - Cloud Knowledge Management System',
          description: [
            {
              point: 'Lead the frontend development of a cloud-based knowledge management system.',
            },
            {
              point:
                'Utilized Vue.js, Node.js, JavaScript, HTML, CSS, SCSS, Material Design to build a scalable and responsive application.',
            },
            {
              point:
                'Collaborated with cross-functional teams using Git, SourceTree, and Azure DevOps for version control and project management.',
            },
          ],
          from: '01/2023',
          to: 'Present',
          color: 'light-green',
        },
        {
          title: 'Junior Full Stack Developer',
          subtitle: 'Moyae - Electronic Health Record System',
          description: [
            {
              point:
                'Developed full-stack web applications, working with React.js, Node.js, and PostgreSQL.',
            },
            {
              point:
                'Implemented modern frontend technologies including Redux, MUI, and Prisma to enhance user experience and app performance.',
            },
            {
              point:
                'Contributed to the development of scalable and maintainable code for various features.',
            },
          ],
          from: '03/2022',
          to: '06/2022',
          color: 'light-green',
        },
      ]
    },
  },
  watch: {},
}
</script>

<style scoped></style>
