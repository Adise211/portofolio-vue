<template>
  <v-container fluid style="height: 100vh">
    <v-row class="align-center justify-center fill-height">
      <!-- Send Email -->
      <v-col>
        <v-card elevation="5" :class="{ 'bg-grey-lighten-3': isDarkMode }">
          <v-card-title class="text-h5 mb-5 font-weight-bold">Send Me A Message</v-card-title>
          <v-card-text style="height: 70vh">
            <v-row>
              <v-col>
                <v-text-field label="Your Name" variant="outlined"></v-text-field>
              </v-col>
              <v-col>
                <v-text-field label="Email" variant="outlined"></v-text-field>
              </v-col>
            </v-row>
            <v-row>
              <v-col cols="10">
                <v-text-field label="Subject" variant="outlined"></v-text-field>
              </v-col>
            </v-row>
            <v-row>
              <v-col cols="10">
                <v-textarea label="Your message here..." variant="outlined"></v-textarea>
              </v-col>
            </v-row>
            <v-row>
              <v-btn
                class="mx-2 rounded-xl mt-5 ml-3"
                :color="isDarkMode ? 'light-green' : 'black'"
                size="large"
                >Send Message</v-btn
              >
            </v-row>
          </v-card-text>
        </v-card>
      </v-col>
      <!-- Personal Info -->

      <v-col cols="12" md="4">
        <v-card elevation="5" class="bg-grey-lighten-3">
          <v-card-title class="text-h5 font-weight-bold">Contact Information</v-card-title>
          <v-card-text style="height: 30vh">
            <v-list class="bg-grey-lighten-3">
              <v-list-item>
                <v-btn
                  color="light-green"
                  icon="mdi-email"
                  size="small"
                  variant="tonal"
                  class="cursor-default mr-3"
                ></v-btn>
                <span>adisemamo211@gmail.com</span>
              </v-list-item>
              <v-list-item>
                <v-btn
                  color="light-green"
                  icon="mdi-phone"
                  size="small"
                  variant="tonal"
                  class="cursor-default mr-3 mt-3"
                ></v-btn>
                <span>516-838-***</span>
              </v-list-item>
              <v-list-item>
                <v-btn
                  color="light-green"
                  icon="mdi-map-marker-outline"
                  size="small"
                  variant="tonal"
                  class="cursor-default mr-3 mt-3"
                ></v-btn>
                <span>Jacksonville, Florida, USA</span>
              </v-list-item>
            </v-list>
          </v-card-text>
        </v-card>
        <v-card elevation="5" class="mt-5" :class="{ 'bg-grey-lighten-3': isDarkMode }">
          <v-card-title class="text-h5 font-weight-bold mb-5">Availability</v-card-title>

          <v-card-text style="height: 17vh">
            <span
              >Currently available for freelance projects and full-time positions
              opportunities.</span
            >
            <p class="mt-5 font-weight-bold">
              Response time: <span class="text-light-green font-weight-medium">24-48 hours</span>
            </p>
          </v-card-text>
        </v-card>
      </v-col>
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
  },
  data: () => ({}),
  created() {},
  mounted() {},
  methods: {},
  computed: {},
  watch: {},
}
</script>

<style scoped></style>
