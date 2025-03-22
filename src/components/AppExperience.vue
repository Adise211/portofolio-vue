<template>
  <v-container fluid class="pa-0">
    <v-timeline v-if="!isMobile" class="align-start" truncate-line="start">
      <v-timeline-item v-for="(item, i) in items" :key="i" :dot-color="item.color" fill-dot>
        <v-card elevation="5" :class="{ 'bg-grey-lighten-3': isDarkMode }">
          <v-card-title class="d-flex align-center flex-wrap" :class="`bg-${item.color}`">
            <span>{{ item.title }}</span>
            <v-spacer></v-spacer>
            <span class="text-subtitle-2">{{ item.from }} - {{ item.to }}</span>
          </v-card-title>
          <v-card-subtitle :class="`bg-${item.color}`">{{ item.subtitle }}</v-card-subtitle>
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
    <div v-else class="d-flex flex-column justify-space-around">
      <div class="page-title text-h4 mb-15 mt-2 text-center">
        <span>Experience</span>
      </div>
      <template v-for="(item, i) in items" :key="i">
        <v-card elevation="5" :class="[{ 'bg-grey-lighten-3': isDarkMode }]" class="mb-15">
          <v-card-title class="d-flex align-center flex-wrap" :class="`bg-${item.color}`">
            <span>{{ item.title }}</span>
            <v-spacer></v-spacer>
            <span class="text-subtitle-2">{{ item.from }} - {{ item.to }}</span>
          </v-card-title>
          <v-card-subtitle :class="`bg-${item.color}`">{{ item.subtitle }}</v-card-subtitle>
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
      </template>
    </div>
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
          color: 'amber-lighten-2',
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
          color: 'purple-lighten-2',
        },
        {
          title: 'Medical Center Representative ',
          subtitle: 'Sharan - Home Medical Services',
          description: [
            {
              point:
                'Delivered compassionate care and support to patients with various health conditions, ensuring a personalized and positive experience',
            },
            {
              point:
                'Coordinated and managed appointments between patients and healthcare professionals, including doctors and nurses, to optimize care delivery.',
            },
            {
              point:
                'Acted as a liaison between patients and medical assistants, facilitating seamless integration of care services and ensuring all patient needs were addressed.',
            },
            // {
            //   point:
            //     'Supported the overall healthcare team to ensure efficient patient care and effective communication across all departments.',
            // },
          ],
          from: '04/2019',
          to: '04/2020',
          color: 'red-lighten-2',
        },
        {
          title: 'Army Medic',
          subtitle: 'IDF - Israel Defense Forces',
          description: [
            {
              point:
                'Provided emergency medical care to injured soldiers, ensuring prompt and effective treatment in high-pressure situations.',
            },
            {
              point:
                'Delivered routine and emergency healthcare to sick soldiers, managing their recovery and promoting overall well-being.',
            },
            {
              point:
                'Implemented and enforced preventive health measures to control the spread of infectious diseases within the base, contributing to the health and safety of all personnel.',
            },
            // {
            //   point:
            //     'Collaborated with medical teams and military leadership to ensure comprehensive and efficient healthcare delivery in a fast-paced environment.',
            // },
          ],
          from: '03/2016',
          to: '04/2018',
          color: 'light-green',
        },
      ]
    },
  },
  watch: {},
}
</script>

<style scoped></style>
