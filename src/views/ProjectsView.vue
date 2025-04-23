<script setup lang="ts">
  import {ref} from "vue";

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

  interface Day {
    title: string;
    content: string;
  }

  const days = ref<Day[]>([
    {
      title: 'Dag 1 – Introductie AI & BTP',
      content: `
        Op de eerste dag kregen we een theoretische inleiding over:
        - De geschiedenis van Artificiële Inteleligentie
        - De evolutie van SAP van ERP naar Business Technology Platform
        - De bouwstenen van BTP: ontwikkel-, integratie- en analysetools in de cloud
        `,
    },
    {
      title: 'Dag 2 – Probleemoplossing PXL',
      content: `
        We stelden ons de vragen:
        1. Wat is het doel van PXL?
        2. Wie zijn de externe actoren?
        3. Wat zijn de belangrijkste irritaties?

        Uitkomst: een AI-applicatie die data uit documenten haalt en deadlines automatisch in een centrale kalender zet, plus notificaties wanneer een deadline nadert.
        `,
    },
    {
      title: 'Dag 3 – Bouw & Presentatie',
      content: `
        - In groepen van drie: low-code app bouwen met SAP Build en AI-assistent Joule
        - Ons project: voorraadbeheer-app voor autoverkopers (merk, model, bouwjaar, km-stand)
        - Slotpresentatie: leerpunten rond prompt-engineering en presentatievaardigheden + feedback van begeleiders
        `,
    },
  ]);
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
<!--    <p class="text-xl md:text-2xl font-light opacity-80">-->
<!--      Placeholder text voor de innovatieroute sectie. Hier komt informatie over de innovatieroute.-->
<!--    </p>-->
    <div class="max-w-3xl mx-auto space-y-4 text-black mt-4">
      <details
          v-for="(day, idx) in days"
          :key="idx"
          class="bg-white/80 bg-opacity-10 p-6 rounded-2xl shadow-lg backdrop-blur-md"
      >
        <summary class="cursor-pointer text-2xl font-semibold">
          {{ day.title }}
        </summary>
        <div class="mt-4 text-left text-black whitespace-pre-line">
          {{ day.content }}
        </div>
      </details>
    </div>
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