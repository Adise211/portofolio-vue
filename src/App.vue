<template>
  <v-app :theme="isDarkMode ? 'dark' : 'light'">
    <!-- Drawer for Mobile View -->
    <v-navigation-drawer v-if="!isMobile" app permanent>
      <v-list dense>
        <v-list-item height="35vh" class="d-flex align-center justify-center">
          <v-img width="300%" height="300%" cover :src="profilePhoto" rounded="circle"></v-img>
          <div class="text-h5 mt-4">Adise Mamoye</div>
        </v-list-item>
        <v-divider></v-divider>
        <v-list-item height="8vh" @click="scrollToSection(sections.about)" class="nav-item">
          <v-list-item-title>About</v-list-item-title>
        </v-list-item>
        <v-divider></v-divider>
        <v-list-item height="8vh" @click="scrollToSection(sections.experience)" class="nav-item">
          <v-list-item-title>Experience</v-list-item-title>
        </v-list-item>
        <v-divider></v-divider>
        <v-list-item height="8vh" @click="scrollToSection(sections.projects)" class="nav-item">
          <v-list-item-title>Projects</v-list-item-title>
        </v-list-item>
        <v-divider></v-divider>
        <v-list-item height="8vh" @click="scrollToSection(sections.skills)" class="nav-item">
          <v-list-item-title>My Skills</v-list-item-title>
        </v-list-item>
        <v-divider></v-divider>
        <v-list-item height="8vh" @click="scrollToSection(sections.contact)" class="nav-item">
          <v-list-item-title>Contact</v-list-item-title>
        </v-list-item>
        <v-divider></v-divider>
        <v-list-item class="nav-item">
          <div>
            <v-icon class="mr-1" @click="goToLinkedIn">mdi-linkedin</v-icon>
            <v-icon class="ml-1" @click="goToGithub">mdi-github</v-icon>
          </div>
        </v-list-item>
      </v-list>
      <v-spacer></v-spacer>
      <v-switch
        v-model="isDarkMode"
        class="d-flex justify-center mt-10"
        size="small"
        append-icon="mdi-weather-night"
        prepend-icon="mdi-weather-sunny"
        density="compact"
        hide-details
      ></v-switch>
    </v-navigation-drawer>

    <!-- Main Content -->
    <v-main>
      <v-container class="fill-height d-block">
        <v-window v-model="sectionId" class="fill-height">
          <v-window-item :value="sections.about" class="fill-height">
            <v-lazy
              :options="{ threshold: 1 }"
              transition="slide-x-reverse-transition"
              class="fill-height"
            >
              <section
                id="about"
                class="d-flex flex-column justify-start fill-height mt-10"
                :class="{ 'ml-10': !isMobile }"
              >
                <div class="text-h2">Hi,</div>
                <div class="text-h2">I'm Adise</div>
                <div v-if="!isMobile" class="intro-title text-h3 mt-5">
                  <div class="intro-title-wrapper text-light-green">
                    <div className="intro-title-item">Full Stack Developer</div>
                    <div className="intro-title-item">Web Developer</div>
                    <div className="intro-title-item">Frontend Developer</div>
                    <div className="intro-title-item">Backend Developer</div>
                  </div>
                </div>
                <div
                  class="into-description text-h5 pt-8 mt-16 text-center align-self-center"
                  :class="!isMobile ? ' w-75' : 'w-100'"
                >
                  I develop and design applications that are intuitive, functional, and visually
                  appealing, with a focus on creating exceptional user experiences
                </div>

                <v-row class="d-flex justify-center" :class="!isMobile ? 'mt-7' : 'mt-14'">
                  <v-col cols="12" md="auto" :class="{ 'text-center': isMobile }">
                    <v-btn
                      class="mx-2 rounded-xl"
                      :class="{ 'mb-3': isMobile }"
                      :color="isDarkMode ? 'light-green' : 'black'"
                      size="large"
                      @click="scrollToSection(sections.projects)"
                      >View Projects</v-btn
                    >
                    <v-btn
                      class="mx-2 rounded-xl"
                      variant="outlined"
                      size="large"
                      @click="scrollToSection(sections.contact)"
                      >Contact Me</v-btn
                    >
                  </v-col>
                </v-row>
                <v-row v-if="isMobile" class="text-center">
                  <v-col cols="12">
                    <v-icon class="scroll-arrow" size="x-large"> mdi-arrow-right </v-icon>
                  </v-col>
                </v-row>
              </section>
            </v-lazy>
          </v-window-item>
          <v-window-item :value="sections.experience" class="my-auto">
            <section id="experience">
              <AppExperience :isDarkMode="isDarkMode" :isMobile="isMobile"></AppExperience>
            </section>
          </v-window-item>
          <v-window-item :value="sections.projects" class="fill-height">
            <section id="projects" class="fill-height">
              <AppProjects :isDarkMode="isDarkMode" :isMobile="isMobile"></AppProjects>
            </section>
          </v-window-item>
          <v-window-item :value="sections.skills" class="fill-height">
            <section id="skills" class="fill-height">
              <AppSkills :isMobile="isMobile"></AppSkills>
            </section>
          </v-window-item>
          <v-window-item :value="sections.contact" class="fill-height">
            <section id="contact" class="fill-height">
              <AppContact :isDarkMode="isDarkMode" :isMobile="isMobile"></AppContact>
            </section>
          </v-window-item>
        </v-window>
      </v-container>
    </v-main>
  </v-app>
</template>

<script>
import AppExperience from './components/AppExperience.vue'
import AppProjects from './components/AppProjects.vue'
import AppSkills from './components/AppSkills.vue'
import AppContact from './components/AppContact.vue'

export default {
  components: { AppExperience, AppProjects, AppSkills, AppContact },
  data() {
    return {
      isDarkMode: true, // Dark Mode toggle
      sectionId: 'intro',
      sections: {
        about: 'about',
        experience: 'experience',
        projects: 'projects',
        skills: 'skills',
        contact: 'contact',
      },
    }
  },
  mounted() {},
  methods: {
    scrollToSection(section) {
      this.sectionId = section

      // const element = document.getElementById(subSection)
      // if (element) {
      //   window.scrollTo({
      //     top: element.offsetTop,
      //     behavior: 'smooth',
      //   })
      // }
    },
    goToLinkedIn() {
      window.open('https://www.linkedin.com/in/adise-mamoye-15876a240')
    },
    goToGithub() {
      window.open('https://github.com/Adise211')
    },
  },
  computed: {
    isMobile() {
      return this.$vuetify.display.mobile
    },
    profilePhoto() {
      return 'images/profile_photo.png'
    },
  },
  watch: {},
}
</script>

<style>
.intro-title {
  height: 50px;
  overflow: hidden;
}

.intro-title-wrapper {
  height: 100%;
  animation: move 10s ease-in-out infinite alternate;
}

@keyframes move {
  25% {
    transform: translateY(-50px);
  }
  50% {
    transform: translateY(-100px);
  }
  75% {
    transform: translateY(-150px);
  }
  100% {
    transform: translateY(-200px);
  }
}

.intro-title-item {
  height: 50px;
  /* font-size: 30px; */
  font-weight: bold;
  /* color: yellowgreen; */
  display: flex;
  align-items: center;
}

.nav-item {
  text-align: center;
  height: 10vh;
}

.scroll-arrow {
  animation: bounce 1.5s infinite;
  cursor: pointer;
  color: rgb(156 163 175 / 1) !important;
}

.arrow-btn {
  background-color: rgba(0, 0, 0, 0.5);
  color: white;
  border-radius: 50%;
  box-shadow: 0 2px 10px rgba(0, 0, 0, 0.2);
}

.arrow-btn:hover {
  background-color: rgba(0, 0, 0, 0.7);
}
/* Bounce animation */
@keyframes bounce {
  0% {
    transform: translateX(0);
  }
  50% {
    transform: translateX(15px);
  }
  100% {
    transform: translateX(0);
  }
}
</style>
