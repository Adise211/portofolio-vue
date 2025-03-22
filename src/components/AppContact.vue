<template>
  <v-container fluid class="fill-height">
    <v-row v-if="isMobile" class="page-title text-h4 mb-15 mt-2">
      <span class="mx-auto">Contact</span>
    </v-row>
    <v-row class="align-center justify-center fill-height">
      <!-- Send Email -->
      <v-col cols="12" md="8">
        <v-card
          elevation="5"
          :class="{ 'bg-grey-lighten-3': isDarkMode }"
          :max-height="isMobile ? '108vh' : ''"
          :min-height="isMobile ? '85vh' : ''"
        >
          <v-card-title class="text-h5 mb-5 font-weight-bold">Send Me A Message</v-card-title>
          <v-card-text>
            <v-form ref="form" id="form">
              <v-row>
                <v-col cols="12" md="6">
                  <v-text-field
                    v-model="name"
                    label="Your Name"
                    variant="outlined"
                    type="text"
                    name="user_name"
                    :rules="[formRules.required]"
                    validate-on="submit"
                  ></v-text-field>
                </v-col>
                <v-col cols="12" md="6">
                  <v-text-field
                    v-model="email"
                    label="Email"
                    variant="outlined"
                    type="email"
                    name="user_email"
                    :rules="[formRules.required, formRules.emailMatch]"
                    validate-on="submit"
                  ></v-text-field>
                </v-col>
              </v-row>
              <v-row>
                <v-col cols="12" md="10">
                  <v-text-field
                    v-model="subject"
                    label="Subject"
                    variant="outlined"
                    type="text"
                    name="user_subject"
                    :rules="[formRules.required]"
                    validate-on="submit"
                  ></v-text-field>
                </v-col>
              </v-row>
              <v-row>
                <v-col cols="12" md="10">
                  <v-textarea
                    v-model="message"
                    label="Your message here..."
                    variant="outlined"
                    name="message"
                    :rules="[formRules.required]"
                    validate-on="submit"
                  ></v-textarea>
                </v-col>
              </v-row>
            </v-form>
          </v-card-text>
          <v-card-actions class="align-end mb-3">
            <v-btn
              class="mx-2 rounded-xl mt-5 ml-3"
              :color="isDarkMode ? 'light-green' : 'black'"
              size="large"
              @click.prevent="sendMessage"
              variant="flat"
              >Send Message</v-btn
            >
            <span>
              <v-alert
                v-if="alertType || alertMessage"
                :text="alertMessage"
                :type="alertType"
                variant="tonal"
                density="compact"
              ></v-alert>
            </span>
          </v-card-actions>
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
            <span>Currently available for freelance projects and full-time positions.</span>
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
const emailJs = window.emailjs

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
  data: () => ({
    name: '',
    email: '',
    subject: '',
    message: '',
    alertType: '',
    alertMessage: '',
  }),
  created() {},
  mounted() {},
  methods: {
    async sendMessage() {
      const { valid } = await this.$refs.form.validate()
      if (valid) {
        const response = await emailJs.sendForm(
          import.meta.env.VITE_EMAIL_JS_SERVICE_ID,
          import.meta.env.VITE_EMAIL_JS_TEMPLATE_ID,
          'form',
          { publicKey: import.meta.env.VITE_EMAIL_JS_PUBLIC_KEY },
        )

        if (response.status == 200) {
          // success message
          this.alertType = 'success'
          this.alertMessage = 'message was sent'
          this.$refs.form.reset()
        } else {
          //error message
          this.alertType = 'error'
          this.alertMessage = 'something went wrong'
        }
      }
    },
  },
  computed: {
    formRules() {
      const emailRegex = new RegExp(/^[\w-\\.]+@([\w-]+\.)+[\w-]{2,4}$/)

      return {
        required: (value) => !!value || 'Required',
        emailMatch: (value) => emailRegex.test(value) || 'Invalid e-mail',
      }
    },
  },
  watch: {},
}
</script>

<style scoped></style>
