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
      class="flex flex-col items-center justify-center text-center md:text-left h-screen text-white px-4"
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
           text-white px-4 max-w-7xl mx-auto"
  >
    <img
        src="@/assets/harleen.jpg"
        alt="Foto van Harleen Bhandal"
        class="w-40 h-40 rounded-full mb-6"
    />
    <h1 class="text-5xl md:text-6xl font-extrabold mb-4">
      Over mij
    </h1>
    <p class="text-xl md:text-2xl font-light opacity-80">
      Mijn naam is Harleen Bhandal en ik ben 20 jaar oud. Ik studeer Toegepaste Informatica met een specialisatie in applicatieontwikkeling. Wat mij typeert is mijn brede interesse in zowel de auto-industrie als softwareontwikkeling. Dit zijn twee domeinen die elkaar steeds meer raken door technologische innovatie.
      <br />
      <br />
      Ik beschouw mezelf als een meewerkend teamlid dat pragmatisch te werk gaat. In projecten focus ik me graag op concrete resultaten. Hoewel ik eerder afstandelijk overkom, ben ik betrouwbaar en doelgericht in mijn samenwerking met anderen.
      <br />
      <br />
      Mijn ambitie is om software te ontwikkelen binnen de auto-industrie bijvoorbeeld voor infotainmentsystemen, rijhulpsystemen of voertuigcommunicatie. Om die ambitie waar te maken wil ik graag Duits leren, aangezien het een belangrijke taal is binnen de Europese auto-industrie.
    </p>
    <RouterLink
        to="/projects"
        class="inline-block bg-white bg-opacity-20 hover:bg-opacity-30
               px-6 py-3 rounded-full font-semibold transition text-black mt-20"
    >
      Bekijk mijn activiteiten
    </RouterLink>
  </section>
</template>
<style scoped>
  html {
    scroll-behavior: smooth;
  }
</style>

