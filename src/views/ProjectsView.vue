<script setup lang="ts">
  function scrollToHackathon() {
    const hackathonSection = document.getElementById("hackathon");
    if (hackathonSection) {
      hackathonSection.scrollIntoView({ behavior: "smooth" });
    }
  }
  function scrollToStudyTrip() {
    const studyTripSection = document.getElementById("studytrip");
    if (studyTripSection) {
      studyTripSection.scrollIntoView({ behavior: "smooth" });
    }
  }
</script>

<template>
  <RouterLink
      to="/"
      class="fixed bg-white bg-opacity-20 hover:bg-opacity-30 px-6 py-3 rounded-full font-semibold transition text-black ml-4"
  >
    Terug naar Home
  </RouterLink>

  <div class="w-full content-center items-center justify-center text-center mt-4">
    <h1 class="text-5xl md:text-6xl font-extrabold mb-4 text-white">Activiteiten</h1>
  </div>
  <section
      id="innovatieroute"
      class="flex flex-col items-center justify-center text-center h-screen text-white px-4"
  >
    <h1 class="text-5xl md:text-6xl font-extrabold mb-4">
      Innovatieroute: genAi
    </h1>
    <p class="text-xl md:text-2xl font-light opacity-80">
      Placeholder text voor de innovatieroute sectie. Hier komt informatie over de innovatieroute.
    </p>
    <button
        @click="scrollToHackathon"
        class="inline-block border-2 border-white border-opacity-50 mt-4
               hover:border-blue-500 hover:bg-white hover:text-black px-6 py-3 rounded-full font-semibold transition"
    >
      Hackathon: HackTheFuture
    </button>
  </section>
  <section
      id="hackathon"
      class="flex flex-col items-center justify-center text-cente h-screen text-white px-4"
  >
    <h1 class="text-5xl md:text-6xl font-extrabold mb-4">
      Hackathon: HackTheFuture
    </h1>
    <p class="text-xl md:text-2xl font-light opacity-80">
      Placeholder text voor de hackathon sectie. Hier komt informatie over de hackathon + foto's
    </p>
    <button
        @click="scrollToStudyTrip"
        class="inline-block border-2 border-white border-opacity-50 mt-4
               hover:border-blue-500 hover:bg-white hover:text-black px-6 py-3 rounded-full font-semibold transition"
    >
      Studiereis: Linz
    </button>
  </section>
  <section
      id="studytrip"
      class="flex flex-col items-center justify-center text-cente h-screen text-white px-4"
  >
    <h1 class="text-5xl md:text-6xl font-extrabold mb-4">
      Studiereis: Linz
    </h1>
    <p class="text-xl md:text-2xl font-light opacity-80">
      Placeholder text voor de Studiereis sectie.
    </p>
  </section>
</template>

<style scoped>

</style>