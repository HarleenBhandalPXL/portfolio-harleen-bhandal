<script setup lang="ts">
  function scrollToAboutMe() {
    const aboutMeSection = document.getElementById("about-me");
    if (aboutMeSection) {
      aboutMeSection.scrollIntoView({ behavior: "smooth" });
    }
  }
</script>

<template>
  <section
      class="flex flex-col items-center justify-center text-center h-screen text-white px-4"
  >
    <h1 class="text-5xl md:text-6xl font-extrabold mb-4">
      Ik ben Harleen Bhandal
    </h1>
    <h2 class="text-2xl md:text-3xl font-medium mb-2 opacity-90">
      Student Toegepaste Informatica
    </h2>
    <h3 class="text-xl md:text-2xl font-light opacity-80">
      Applicatieontwikkeling
    </h3>
    <div class="mt-8 space-x-4">
      <RouterLink
          to="/projects"
          class="inline-block bg-white bg-opacity-20 hover:bg-opacity-30
               px-6 py-3 rounded-full font-semibold transition text-black"
      >
        Bekijk mijn activiteiten
      </RouterLink>
      <button
          @click="scrollToAboutMe"
          class="inline-block border-2 border-white border-opacity-50
               hover:border-blue-500 hover:bg-white hover:text-black px-6 py-3 rounded-full font-semibold transition"
      >
        Over mij
      </button>
    </div>
  </section>
  <section
      id="about-me"
      class="flex flex-col items-center justify-center text-center
           h-screen bg-gradient-to-br
           text-white px-4"
  >
    <h1 class="text-5xl md:text-6xl font-extrabold mb-4">
      Over mij
    </h1>
    <p class="text-xl md:text-2xl font-light opacity-80">

    </p>
  </section>
</template>
<style scoped>
  html {
    scroll-behavior: smooth;
  }
</style>

