<template>
  <v-app theme="light">
    <!-- Drawer for Mobile View -->
    <v-navigation-drawer app permanent>
      <v-list dense>
        <v-list-item height="35vh" class="d-flex align-center justify-center">
          <v-img width="300%" height="300%" cover :src="profilePhoto" rounded="circle"></v-img>
          <div class="text-h5 mt-4">Adise Mamoye</div>
        </v-list-item>
        <v-divider></v-divider>
        <v-list-item @click="scrollToSection('about')" class="nav-item">
          <v-list-item-title>About</v-list-item-title>
        </v-list-item>
        <v-divider></v-divider>

        <v-list-item @click="scrollToSection('projects')" class="nav-item">
          <v-list-item-title>Projects</v-list-item-title>
        </v-list-item>
        <v-divider></v-divider>

        <v-list-item @click="scrollToSection('skills')" class="nav-item">
          <v-list-item-title>My Skills</v-list-item-title>
        </v-list-item>
        <v-divider></v-divider>

        <v-list-item @click="scrollToSection('contact')" class="nav-item">
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
    </v-navigation-drawer>

    <!-- Main Content -->
    <v-main>
      <v-container>
        <section id="about" class="mt-10 ml-10 d-flex flex-column justify-start">
          <div class="text-h2">Hi,</div>
          <div class="text-h2">I'm Adise</div>
          <div class="intro-title text-h3 mt-5">
            <div class="intro-title-wrapper">
              <div className="intro-title-item">Full Stack Developer</div>
              <div className="intro-title-item">Web Developer</div>
              <div className="intro-title-item">Frontend Developer</div>
              <div className="intro-title-item">Backend Developer</div>
            </div>
          </div>
          <div class="into-description text-h5 pt-8 mt-16 text-center w-75 align-self-center">
            I develop and design applications that are intuitive, functional, and visually
            appealing, with a focus on creating exceptional user experiences
          </div>

          <v-row class="d-flex justify-center mt-8">
            <v-col cols="auto">
              <v-btn class="mx-2 rounded-xl" color="black" size="large">View Projucts</v-btn>
              <v-btn class="mx-2 rounded-xl" variant="outlined" size="large">Contact Me</v-btn>
            </v-col>
          </v-row>
          <v-row class="d-flex justify-center mt-10">
            <v-col cols="auto">
              <v-icon class="scroll-arrow" size="x-large"> mdi-arrow-down </v-icon>
            </v-col>
          </v-row>
        </section>

        <section id="projects">
          <!-- <h1>Projects</h1> -->
          <!-- Add your content here -->
        </section>

        <section id="skills">
          <!-- <h1>Skills</h1> -->
          <!-- Add your content here -->
        </section>

        <section id="contact">
          <!-- <h1>Contact</h1> -->
          <!-- Add your content here -->
        </section>
      </v-container>
    </v-main>
  </v-app>
</template>

<script>
export default {
  data() {
    return {
      darkMode: false, // Dark Mode toggle
    }
  },
  mounted() {},
  methods: {
    scrollToSection(section) {
      const element = document.getElementById(section)
      if (element) {
        window.scrollTo({
          top: element.offsetTop,
          behavior: 'smooth',
        })
      }
    },
    goToLinkedIn() {
      window.open('https://www.linkedin.com/in/adise-mamoye-15876a240')
    },
    goToGithub() {
      window.open('https://github.com/Adise211')
    },
  },
  computed: {
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
  color: greenyellow;
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

/* Bounce animation */
@keyframes bounce {
  0% {
    transform: translateY(0);
  }
  50% {
    transform: translateY(10px);
  }
  100% {
    transform: translateY(0);
  }
}
</style>
