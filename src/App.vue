<template>
  <v-app>
    <!-- Drawer for Mobile View -->
    <v-navigation-drawer app permanent>
      <v-list dense>
        <v-list-item>
          <div>Adise Mamoye</div>
        </v-list-item>
        <v-list-item @click="scrollToSection('about')">
          <v-list-item-title>About</v-list-item-title>
        </v-list-item>
        <v-list-item @click="scrollToSection('projects')">
          <v-list-item-title>Projects</v-list-item-title>
        </v-list-item>
        <v-list-item @click="scrollToSection('skills')">
          <v-list-item-title>Skills</v-list-item-title>
        </v-list-item>
        <v-list-item @click="scrollToSection('contact')">
          <v-list-item-title>Contact</v-list-item-title>
        </v-list-item>
      </v-list>
    </v-navigation-drawer>

    <!-- Main Content -->
    <v-main>
      <v-container>
        <section id="about">
          <h1>About Me</h1>
          <!-- Add your content here -->
        </section>

        <section id="projects">
          <h1>Projects</h1>
          <!-- Add your content here -->
        </section>

        <section id="skills">
          <h1>Skills</h1>
          <!-- Add your content here -->
        </section>

        <section id="contact">
          <h1>Contact</h1>
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
  },
}
</script>

<style>
/* You can customize your App Bar styling here */
.v-toolbar-title {
  font-weight: bold;
}

.v-btn {
  color: #fff;
}
</style>
