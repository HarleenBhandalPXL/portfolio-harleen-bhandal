<script setup lang="ts">
  import {ref} from "vue";
  import hackathon1 from '@/assets/hackathon_1.jpg';
  import hackathon2 from '@/assets/hackathon_2.png';
  import hackathon3 from '@/assets/hackathon_3.jpg';

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

  function scrollToFinalReflection() {
    const finalReflection = document.getElementById("final-reflection");
    if (finalReflection) {
      finalReflection.scrollIntoView({ behavior: "smooth" });
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
        - De geschiedenis van Artificiële Intelligentie
        - De evolutie van SAP van ERP naar Business Technology Platform
        - De bouwstenen van BTP
        `,
    },
    {
      title: 'Dag 2 – Oplossing zoeken voor een probleem binnen PXL',
      content: `
        We kozen ervoor om het probleem aan te pakken dat deadlines moeilijk centraal te vinden zijn.

        We stelden ons de vragen:
        1. Wat is het doel van PXL?
        2. Wie zijn de externe actoren?
        3. Wat zijn de belangrijkste irritaties?

        Uitkomst: een AI-applicatie die data uit documenten haalt en deadlines automatisch in een centrale kalender zet. Daarnaast zou het ook handig zijn als er een notificatie wordt verstuurd wanneer er een deadline nadert.
        `,
    },
    {
      title: 'Dag 3 – Presentatie',
      content: `
        - In groepen van drie: low-code app bouwen met SAP Build en AI-assistent Joule
        - Ons project: voorraadbeheer voor autoverkopers (merk, model, bouwjaar, km-stand)
        - Slotpresentatie: leerpunten rond prompt-engineering en presentatievaardigheden + feedback van begeleiders
        `,
    },
  ]);

  const isAnyDropdownOpen = ref(false);

  function handleDropdownToggle(isOpen: boolean) {
    isAnyDropdownOpen.value = isOpen;
  }

  const showModalInnovation = ref(false);
  function openModalInnovation() {
    showModalInnovation.value = true;
  }
  function closeModalInnovation() {
    showModalInnovation.value = false;
  }

  const hackathonParagraphs = ref<Day[]>([
    {
      title: 'Challenge 1: Ontrafel het protocol',
      content: `We moesten binaire berichten decoderen van een verloren ruimteschip met protocol een protocol genaamd S2SMP. We gebruikten .NET en HttpClient om de binaire data te valideren en om te zetten naar leesbare tekst.`,
    },
    {
      title: 'Challenge 2: Ontrafel de QR code',
      content:
          'De bedoeling was om een beschadigde keypas te herstellen via de API. We ontdekten dat de service drie mogelijke vragen hergebruikte en daar het juiste antwoord bij terugraf. Door meerdere requests te sturen verzamelden we alle antwoorden en stuurden we het juiste antwoord binnen 4 seconden in. Hoewel dit niet de bedoeling van de challenge was, hebben we van deze onverwachte ontdekking geprofiteerd om de taak succesvol te voltooien.',
    },
    {
      title: 'Challenge 3: Navigeer door de ruimte',
      content: 'De kortste en langste route berekenen tussen waypoints. Met Python en een DFS-algoritme navigeerden we door de graph-structuur uit de API. We berekenden de korste en de langste route en stuurde het resultaat terug.'
    }
  ]);

  const hackathonImages = ref<{ src: string; alt: string }[]>([
    { src: hackathon1, alt: 'Scores' },
    { src: hackathon2, alt: 'Score presentaties' },
    { src: hackathon3, alt: 'Pasje' },
  ]);


  const selectedImage = ref<string | null>(null);

  function openImagePreview(imageSrc: string) {
    selectedImage.value = imageSrc;
  }

  function closeImagePreview() {
    selectedImage.value = null;
  }

  const showModalHackathon = ref(false);
  function openModalHackathon() {
    showModalHackathon.value = true;
  }
  function closeModalHackathon() {
    showModalHackathon.value = false;
  }

  const showModalStudyTrip = ref(false);
  function openModalStudyTrip() {
    showModalStudyTrip.value = true;
  }
  function closeModalStudyTrip() {
    showModalStudyTrip.value = false;
  }

  const studyTripParagraphs = ref<Day[]>([
    {
      title: 'Ars Electronic Center',
      content: `Het Ars Electronica Center is wereldwijd bekend vanwege zijn innovatieve benaderingen van de relatie tussen digitale kunst en de maatschappij. Het centrum biedt een platform voor het verkennen van de rol van technologie in de moderne wereld en hoe kunst kan bijdragen aan het begrijpen van de maatschappelijke impact van technologische ontwikkelingen. `,
    },
    {
      title: 'Hangenberg University',
      content:
          'Deze onderwijsinstelling staat bekend om zijn focus op technologie en informatica en biedt opleidingen die studenten voorbereiden op de technologische uitdagingen van de toekomst. De universiteit maakt gebruik van een projectgerichte aanpak waarbij studenten in teams werken aan projecten. Dit was een waardevolle ervaring omdat het me aanmoedigde om breder te denken over hoe ik technologie kan gebruiken. Niet alleen als een technicus, maar ook als iemand die samenwerkt met andere sectoren om innovatieve oplossingen te creëren.',
    }
  ]);
</script>

<template>
  <RouterLink
      to="/"
      class="fixed bg-white bg-opacity-20 hover:bg-opacity-30 px-6 py-3 rounded-full font-semibold transition text-black ml-4"
  >
    Terug naar Home
  </RouterLink>

  <div class="w-full content-center items-center justify-center text-center relative mt-4 top-20">
    <h1
        class="text-5xl md:text-7xl font-extrabold mb-4 text-white transition-opacity duration-400"
        :class="{ 'opacity-0': isAnyDropdownOpen }"
    >Activiteiten</h1>
  </div>
  <section
      id="innovatieroute"
      class="flex flex-col items-center justify-center text-center h-screen text-white px-4"
  >
    <h1 class="text-5xl md:text-6xl font-extrabold mb-4">
      Innovatieroute: genAi
    </h1>
    <div class="max-w-6xl mx-auto space-y-4 mt-4">
      <p class="text-xl">
        Deze driedaagse innovatieroute van Flexso was gericht op het verkennen van de mogelijkheden van Artificial Intelligence en de Business Technology Platform (BTP) van SAP. Het doel van de workshop was om inzicht te krijgen in de werking van SAP, AI-toepassingen, en BTP.
        Gedurende de workshop hadden we de kans om zelf een applicatie te ontwikkelen met behulp van de AI-assistent Joule en deze op de laatste dag van de workshop te presenteren. Mijn persoonlijke doelstelling was het dieper inzicht krijgen in prompt engineering.
      </p>
    </div>
    <div class="max-w-3xl mx-auto space-y-4 text-black mt-8">
      <details
          v-for="(day, idx) in days"
          :key="idx"
          class="bg-white/80 bg-opacity-10 p-6 rounded-2xl shadow-lg backdrop-blur-md"
          @toggle="handleDropdownToggle($event.target.open)"
      >
        <summary class="cursor-pointer text-2xl font-semibold">
          {{ day.title }}
        </summary>
        <div class="mt-4 text-left text-black whitespace-pre-line">
          {{ day.content }}
        </div>
      </details>
    </div>
    <div class="mt-8 space-x-4">
      <button
          class="inline-block bg-white bg-opacity-20 hover:bg-opacity-30
          px-6 py-3 rounded-full font-semibold transition text-black"
          @click="openModalInnovation"
      >
        Lees heel mijn verslag
      </button>
      <button
          @click="scrollToHackathon"
          class="inline-block border-2 border-white border-opacity-50 mt-10
                 hover:border-blue-500 hover:bg-white hover:text-black px-6 py-3 rounded-full font-semibold transition"
      >
        Hackathon: HackTheFuture
      </button>
    </div>
  </section>
  <transition
      enter-active-class="transition-opacity duration-300"
      enter-from-class="opacity-0"
      enter-to-class="opacity-100"
      leave-active-class="transition-opacity duration-300"
      leave-from-class="opacity-100"
      leave-to-class="opacity-0"
  >
    <div
        v-if="showModalInnovation"
        class="fixed inset-0 bg-black/80 bg-opacity-50 flex items-center justify-center z-50"
    >
      <div class="bg-white rounded-2xl w-11/12 md:w-3/4 lg:w-1/2 max-h-[80vh] overflow-y-auto p-6 relative">
        <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" class="size-6 absolute top-4 right-4 text-red-500 hover:text-red-700"
             @click="closeModalInnovation">
          <path stroke-linecap="round" stroke-linejoin="round" d="M6 18 18 6M6 6l12 12" />
        </svg>
        <h2 class="text-3xl font-bold mb-4">Innovatieroute: genAI</h2>
        <div class="space-y-4 text-left text-gray-800">
          <p>
            Deze driedaagse innovatieroute van Flexso was gericht op het verkennen van de mogelijkheden van Artificial Intelligence en de Business Technology Platform (BTP) van SAP. Het doel van de workshop was om inzicht te krijgen in de werking van SAP, AI-toepassingen, en BTP. Gedurende de workshop hadden we de kans om zelf een applicatie te ontwikkelen met behulp van de AI-assistent Joule en deze op de laatste dag van de workshop te presenteren. Mijn persoonlijke doelstelling was het dieper inzicht krijgen in prompt engineering.
          </p>
          <p>
            De workshop was opgedeeld in drie dagen waarbij elke dag zich richtte op een specifiek onderdeel van de technologieën en tools die we gingen gebruiken. Op de eerste dag kregen we een theoretische inleiding over de geschiedenis van Artificial Intelligence (AI), SAP en de verschillende onderdelen van het Business Technology Platform (BTP). De focus lag op het begrijpen van de basisprincipes van AI en hoe SAP zich heeft ontwikkeld van een eenvoudig ERP-systeem naar een platform dat organisaties helpt om digitale transformatie te realiseren. Daarnaast werd BTP gepresenteerd als het platform dat bedrijven helpt bij het ontwikkelen, integreren en analyseren van applicaties in een cloudomgeving. Deze dag was essentieel om de fundamenten te begrijpen die we later zouden toepassen in de praktijk.
          </p>
          <p>
            Op de tweede dag werkten we met de hele groep aan het oplossen van een probleem dat zich binnen PXL voordeed. We kozen ervoor om het probleem aan te pakken dat deadlines moeilijk centraal te vinden zijn. De deadlines worden namelijk verspreid over verschillende documenten per vak in plaats van in een centrale kalender. Dit vermindert de efficiëntie. We begonnen met een gezamenlijke brainstormsessie om te verkennen hoe we dit probleem konden oplossen. We stelden onszelf de volgende vragen: Wat is het doel van PXL? Wie zijn de externe actoren van een school? Wat zijn de belangrijkste irritaties?
          </p>
          <p>
            Iedereen schreef zijn ideeën op post-its die we vervolgens op een bord plakten. De ideeën werden gecategoriseerd op basis van overeenkomsten waarna we de categorieën bespraken. Aan het einde van de sessie gingen we op zoek naar een mogelijke oplossing met behulp van AI. Het idee dat uit de discussie naar voren kwam was dat AI in staat zou kunnen zijn om datums uit documenten te extraheren en deze deadlines automatisch toe te voegen aan een centrale kalender. Daarnaast zou er een e-mail gestuurd kunnen worden wanneer een deadline nadert.
          </p>
          <p>
            Zoals eerder vermeld kregen we tijdens de workshop de kans om zelf een applicatie te ontwikkelen met behulp van SAP's Business Technology Platform (BTP). Dit gebeurde in groepen van drie waarbij we het Low-code platform SAP Build en het AI-assistentensysteem Joule gebruikten om de app te bouwen. Het doel was om een applicatie te maken die een echt probleem kon oplossen. Ons team besloot een applicatie te ontwikkelen voor een autoverkoper waarmee deze eenvoudig auto's aan de voorraad kon toevoegen. De applicatie hield belangrijke gegevens bij zoals merk, model, bouwjaar en kilometerstand. Hiermee kon de autoverkoper zijn stock efficiënt beheren.
          </p>
          <p>
            De derde dag van de workshop was gericht op het presenteren van de ontwikkelde applicaties. We begonnen de dag met een korte sessie waarin we uitleg kregen over hoe je een effectieve presentatie geeft. Er werd benadrukt dat het belangrijk is om niet alleen de werking van de applicatie te tonen maar ook duidelijk het probleem en de bijbehorende oplossing te verduidelijken. We leerden dat een presentatie goed gestructureerd moet zijn met aandacht voor zowel de inhoud als de manier van communiceren. Het was essentieel om de context van het probleem dat we hadden opgelost goed over te brengen evenals de impact van de gekozen oplossing.
          </p>
          <p>
            Zoals hierboven al werd vermeld hadden we de kans om een applicatie te maken met behulp van Joule. Een van de problemen die hierbij optraden was dat je heel specifiek moet zijn in je communicatie met Joule. Als je niet precies genoeg bent kan het resultaat niet volledig overeenkomen met wat je zoekt, wat ertoe leidt dat je meer tijd kwijt bent om het gewenste resultaat te krijgen. Dit was een waardevolle ervaring omdat het me liet inzien hoe belangrijk het is om gedetailleerde en duidelijke instructies te geven bij het werken met AI.
          </p>
          <p>
            De combinatie van theorie en praktijk was bijzonder leerrijk. We kregen eerst een theoretische uitleg over de tools en technieken die we zouden gebruiken waarna we meteen in de praktijk aan de slag konden. Dit maakte het leren veel effectiever omdat we de opgedane kennis direct konden toepassen. Ik heb geleerd dat het cruciaal is om niet alleen specifiek te zijn maar ook voldoende context te geven aan de AI om het gewenste resultaat te bereiken. Het was interessant om te zien hoe een kleine verandering in de manier waarop we met Joule communiceerden het resultaat aanzienlijk kon beïnvloeden.
          </p>
          <p>
            Ook het presenteren van de applicatie was een belangrijke leerervaring. Het was heel fijn dat we vooraf een kleine sessie kregen waarin presentatievaardigheden werden besproken. Hierdoor waren we beter voorbereid en konden we onze applicatie duidelijk en gestructureerd presenteren. Het gaf ons vertrouwen om de oplossing die we hadden ontwikkeld te presenteren.
          </p>
          <p>
            Na onze presentatie kregen we waardevolle feedback van de begeleiders. De feedback richtte zich op hoe we onze oplossing en de gebruikte technologieën beter konden uitleggen aan een breder publiek. Dit stelde ons in staat om onze presentatievaardigheden verder te verbeteren. De feedback was erg nuttig en gaf ons inzicht om in de toekomst nog effectiever te communiceren en onze toepassingen te presenteren.
          </p>
        </div>
      </div>
    </div>
  </transition>
  <section
      id="hackathon"
      class="flex flex-col items-center justify-center text-cente h-screen text-white px-4"
  >
    <h1 class="text-5xl md:text-6xl font-extrabold mb-4">Hackathon: HackTheFuture</h1>
    <div class="max-w-6xl mx-auto space-y-4 mt-4">
      <p class="text-xl">
        HackTheFuture werd georganiseerd door de Cronos Group. Dit is een organisatie die bestaat uit verschillende bedrijven. Voor de hackathon had ik mij ingeschreven voor de Exsertus Challenge-groep waarbij we in teams van twee aan drie verschillende technische uitdagingen werkten. Elke uitdaging stelde ons voor specifieke problemen die we moesten oplossen.
      </p>
    </div>
    <div class="max-w-3xl mx-auto space-y-4 text-black mt-8">
      <details
          v-for="(day, idx) in hackathonParagraphs"
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
    <div class="grid grid-cols-2 md:grid-cols-3 gap-4 max-w-4xl w-full mt-10">
      <img
          v-for="(img, idx) in hackathonImages"
          :key="idx"
          :src="img.src"
          :alt="img.alt"
          class="w-full h-48 object-cover rounded-xl shadow-lg transform transition-transform duration-200 hover:scale-105 cursor-pointer"
          @click="openImagePreview(img.src)"
      />
    </div>
    <div
        v-if="selectedImage"
        class="fixed inset-0 bg-black bg-opacity-80 flex items-center justify-center z-50"
    >
      <img
          :src="selectedImage"
          alt="Fullscreen Preview"
          class="max-w-full max-h-full rounded-lg"
      />
      <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" class="size-15 absolute top-4 right-4 text-red-500 hover:text-red-700 cursor-pointer"
           @click="closeImagePreview">
        <path stroke-linecap="round" stroke-linejoin="round" d="M6 18 18 6M6 6l12 12" />
      </svg>
    </div>
    <div class="mt-8 space-x-4">
      <button
          class="inline-block bg-white bg-opacity-20 hover:bg-opacity-30
            px-6 py-3 rounded-full font-semibold transition text-black"
          @click="openModalHackathon"
      >
        Lees heel mijn verslag
      </button>
      <button @click="scrollToStudyTrip" class="mt-6 border-2 border-white border-opacity-50 hover:border-blue-500 hover:bg-white hover:text-black px-6 py-3 rounded-full font-semibold transition">
        Studiereis: Linz
      </button>
    </div>
  </section>
  <transition
      enter-active-class="transition-opacity duration-300"
      enter-from-class="opacity-0"
      enter-to-class="opacity-100"
      leave-active-class="transition-opacity duration-300"
      leave-from-class="opacity-100"
      leave-to-class="opacity-0"
  >
    <div
        v-if="showModalHackathon"
        class="fixed inset-0 bg-black/80 bg-opacity-50 flex items-center justify-center z-50"
    >
      <div class="bg-white rounded-2xl w-11/12 md:w-3/4 lg:w-1/2 max-h-[80vh] overflow-y-auto p-6 relative">
        <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" class="size-6 absolute top-4 right-4 text-red-500 hover:text-red-700"
             @click="closeModalHackathon">
          <path stroke-linecap="round" stroke-linejoin="round" d="M6 18 18 6M6 6l12 12" />
        </svg>
        <h2 class="text-3xl font-bold mb-4">Hackathon: HackTheFuture</h2>
        <div class="space-y-4 text-left text-gray-800">
          <p>
            HackTheFuture werd georganiseerd door de Cronos Group. Dit is een organisatie die bestaat uit verschillende bedrijven. Voor de hackathon had ik mij ingeschreven voor de Exsertus Challenge-groep waarbij we in teams van twee aan drie verschillende technische uitdagingen werkten. Elke uitdaging stelde ons voor specifieke problemen die we moesten oplossen.
          </p>
          <p>
            In de eerste challenge moesten we binaire berichten decoderen die afkomstig waren van een verloren ruimteschip. Het gebruikte protocol (S2SMP) had een vast formaat waarbij elk bericht bestond uit een signaaltype, berichttype, coördinaten, berichtinhoud en een afsluitend "END". Onze taak was om de binaire data om te zetten naar leesbare tekst en het juiste antwoord te tonen.
          </p>
          <p>
            Voor de implementatie van deze oplossing kozen we voor .NET als technologie, omdat dit platform ons de benodigde tools biedt om eenvoudig HTTP-aanvragen te doen en we al vertrouwd waren met de programmeertaal. Het stelde ons in staat om de binaire berichten effectief te verwerken en de oplossing op een gestructureerde manier uit te voeren. We maakten gebruik van HttpClient om de berichten op te halen en de antwoorden naar de API te sturen. In de code decoderen we de binaire berichten, valideren we de inhoud en genereren we vervolgens het juiste antwoord.
          </p>
          <p>
            Voor de tweede challenge moesten we een beschadigde keypas herstellen door met de API te communiceren. In eerste instantie stuurden we een request naar de API, waarop we een foutmelding ontvingen samen met het juiste antwoord. Na een paar pogingen kregen we toevallig weer hetzelfde antwoord terug van de API.
          </p>
          <p>
            Door meerdere keren een response te sturen ontdekten we dat de API slechts een pool van drie mogelijke vragen gebruikte, waarvan er willekeurig één werd geselecteerd. We stuurden verschillende requests totdat we de drie verschillende antwoorden hadden verzameld.
          </p>
          <p>
            De uitdaging was vervolgens om binnen een beperkte tijd het juiste antwoord te sturen. Aangezien we de drie mogelijke antwoorden al hadden genoteerd, konden we snel het juiste antwoord vinden zodra we de vraag kregen van de API. We kopieerden en plakten het juiste antwoord en gelukkig was het snel genoeg. We stuurden het binnen vier seconden in.
          </p>
          <p>
            Deze aanpak stelde ons in staat om de QR-code op tijd te ontcijferen. Hoewel dit niet de bedoeling van de challenge was, hebben we van deze onverwachte ontdekking geprofiteerd om de taak succesvol te voltooien.
          </p>
          <p>
            Voor de derde challenge moesten we de kortste en langste route berekenen tussen verschillende waypoints. Gezien de beperkte tijd voor deze uitdaging kozen we ervoor om Python te gebruiken. Python stelde ons in staat om snel een klein script te schrijven waardoor we de oplossing snel konden implementeren.
          </p>
          <p>
            In het begin waren we niet zeker welke algoritmes het meest geschikt zouden zijn om de kortste en langste route tussen twee punten te berekenen. Daarom besloten we eerst ChatGPT te raadplegen om te vragen of er bepaalde algoritmes bestonden die specifiek voor deze taak geschikt waren. GPT stelde voor om het Depth-First Search (DFS) algoritme te gebruiken, wat een effectieve manier is om door een graf te navigeren en het kortste of langste pad te vinden.
          </p>
          <p>
            Met deze suggestie gingen we aan de slag door eerst de gegevens van de API op te halen. De API gaf ons informatie over de waypoints en de verbindingen tussen de punten. Nadat we deze gegevens hadden ontvangen implementeerden we het DFS-algoritme. Dit algoritme doorzocht het graph en berekende de afstand van elke mogelijke route tussen de waypoints.
          </p>
          <p>
            Het DFS-algoritme werkte door recursief door het graph te navigeren, waarbij we bij elk punt de verbindingen naar andere waypoints onderzochten. We hielden de afstand bij en kozen de beste route op basis van de opgegeven eis van de challenge. Dit kon de korste of langste route zijn. Na het berekenen van de juiste route verzonden we deze via een POST-aanvraag naar de API.
          </p>
          <p>
            Ik vond het een bijzonder leerrijke en uitdagende ervaring om deel te nemen aan deze hackathon. De combinatie van tijdsdruk, teamwork en technische vraagstukken zorgde voor een gezonde dosis stress, maar ook voor veel voldoening. Elk moment waarop een oplossing werkte, voelde als een echte overwinning. Het competitieve element gaf de dag extra spanning en zorgde ervoor dat we voortdurend scherp moesten blijven. Samenwerken in een kleine groep onder tijdsdruk dwong ons om efficiënt te communiceren, goed naar elkaar te luisteren en elkaars sterktes optimaal te benutten.
          </p>
          <p>
            Tijdens deze hackathon heb ik vooral geleerd hoe belangrijk het is om onder druk logisch te blijven nadenken en tegelijkertijd creatief te blijven in het vinden van oplossingen. In plaats van te blijven twijfelen over de perfecte aanpak, ontdekte ik dat het vaak beter is om snel een hypothese te testen en van daaruit verder te werken. Ook werd ik me ervan bewust hoe waardevol het is om technische kennis te combineren met probleemoplossend denken. Elke challenge daagde me uit om mijn grenzen te verleggen en nieuwe inzichten op te doen.
          </p>
          <p>
            De hackathon sloot goed aan bij verschillende aspecten van mijn opleiding zoals het werken met API’s, het omgaan met HTTP-verzoeken en het toepassen van algoritmes zoals depth-first search bij het oplossen van routeproblemen. Daarnaast hielp het me om mijn kennis van .NET en Python in de praktijk toe te passen. Door deel te nemen aan deze hackathon kon ik mijn vaardigheden in een realistische en intensieve context verder ontwikkelen en versterken, wat een waardevolle aanvulling is voor mijn opleiding.
          </p>
        </div>
      </div>
    </div>
  </transition>
  <section
      id="studytrip"
      class="flex flex-col items-center justify-center text-cente h-screen text-white px-4"
  >
    <h1 class="text-5xl md:text-6xl font-extrabold mb-4">
      Studiereis: Linz
    </h1>
    <div class="max-w-6xl mx-auto space-y-4 mt-4">
      <p class="text-xl">
        Onze studiereis naar Linz in Oostenrijk werd georganiseerd in samenwerking met de campus Hagenberg van de FH OÖ (Fachhochschule Oberösterreich, of University of Applied Sciences Upper Austria). Deze reis bood ons de gelegenheid om verschillende aspecten van technologie, kunst en cultuur te verkennen.
      </p>
    </div>
    <div class="max-w-3xl mx-auto space-y-4 text-black mt-8">
      <details
          v-for="(day, idx) in studyTripParagraphs"
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
    <div class="mt-8 space-x-4">
      <button
          class="inline-block bg-white bg-opacity-20 hover:bg-opacity-30
          px-6 py-3 rounded-full font-semibold transition text-black"
          @click="openModalStudyTrip"
      >
        Lees heel mijn verslag
      </button>
      <button
          @click="scrollToFinalReflection"
          class="inline-block border-2 border-white border-opacity-50
               hover:border-blue-500 hover:bg-white hover:text-black px-6 py-3 rounded-full font-semibold transition"
      >
        Eindreflectie
      </button>
    </div>
  </section>
  <transition
      enter-active-class="transition-opacity duration-300"
      enter-from-class="opacity-0"
      enter-to-class="opacity-100"
      leave-active-class="transition-opacity duration-300"
      leave-from-class="opacity-100"
      leave-to-class="opacity-0"
  >
    <div
        v-if="showModalStudyTrip"
        class="fixed inset-0 bg-black/80 bg-opacity-50 flex items-center justify-center z-50"
    >
      <div class="bg-white rounded-2xl w-11/12 md:w-3/4 lg:w-1/2 max-h-[80vh] overflow-y-auto p-6 relative">
        <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" class="size-6 absolute top-4 right-4 text-red-500 hover:text-red-700"
             @click="closeModalStudyTrip">
          <path stroke-linecap="round" stroke-linejoin="round" d="M6 18 18 6M6 6l12 12" />
        </svg>
        <h2 class="text-3xl font-bold mb-4">Studiereis: Linz</h2>
        <div class="space-y-4 text-left text-gray-800">
          <p>
            Onze studiereis naar Linz in Oostenrijk werd georganiseerd in samenwerking met de campus Hagenberg van de FH OÖ (Fachhochschule Oberösterreich, of University of Applied Sciences Upper Austria). Deze reis bood ons de gelegenheid om verschillende aspecten van technologie, kunst en cultuur te verkennen.
          </p>
          <p>
            We begonnen de reis met een bezoek aan het Ars Electronica Center, een internationaal bekend en gerespecteerd centrum voor kunst, technologie en samenleving. Het Ars Electronica Center is wereldwijd bekend vanwege zijn innovatieve benaderingen van de relatie tussen digitale kunst en de maatschappij. Het centrum biedt een platform voor het verkennen van de rol van technologie in de moderne wereld en hoe kunst kan bijdragen aan het begrijpen van de maatschappelijke impact van technologische ontwikkelingen.
          </p>
          <p>
            Tijdens ons bezoek kregen we niet alleen de kans om een aantal innovatieve projecten te zien maar ook om dieper in te gaan op de filosofie en de achterliggende ideeën die deze projecten aandreven. De rondleiding was interactief waardoor we onszelf konden onderdompelen in verschillende digitale ervaringen. De gidsen gaven ons een gedetailleerde en informatieve uitleg die ons hielp de complexiteit van de projecten beter te begrijpen. Dit bood ons niet alleen inzicht in de technologische aspecten van de projecten, maar ook in de ethische en maatschappelijke vraagstukken die vaak aan de basis liggen van dergelijke innovaties. Wat vooral opviel was de nadruk die gelegd werd op duurzaamheid en het klimaat. Het Ars Electronica Center integreerde milieubewustzijn in veel van zijn projecten, wat ons liet zien hoe technologie kan bijdragen aan een duurzamere toekomst. Deze focus op het milieu benadrukte de verantwoordelijkheid die we als toekomstige technici en ontwerpers naleven om bij te dragen aan een betere wereld door middel van innovatieve oplossingen.
          </p>
          <p>
            Naast het bezoek aan het Ars Electronica Center was er ook een rondleiding door Hagenberg University. Deze onderwijsinstelling staat bekend om zijn focus op technologie en informatica en biedt opleidingen die studenten voorbereiden op de technologische uitdagingen van de toekomst. De universiteit maakt gebruik van een projectgerichte aanpak waarbij studenten in teams werken aan projecten. Dit maakt het leren niet alleen praktisch, maar ook zeer relevant voor de industrie. We kregen de kans om meer te leren over hun programma's en de manier waarop ze technologie en innovatie in hun onderwijs integreren. Dit was een waardevolle ervaring omdat het me aanmoedigde om breder te denken over hoe ik technologie kan gebruiken. Niet alleen als een technicus, maar ook als iemand die samenwerkt met andere sectoren om innovatieve oplossingen te creëren.
          </p>
          <p>
            Buiten de georganiseerde activiteiten kregen we ook veel vrije tijd om de stad Linz te verkennen. Linz is een prachtige stad met een rijke geschiedenis en cultuur. We maakten gebruik van deze tijd om verschillende bezienswaardigheden te bezoeken. Een van de hoogtepunten was het bezoeken van de indrukwekkende kathedraal in het centrum van de stad. In de avonden gingen we vaak naar cafés.  We genoten niet alleen van de lokale sfeer, maar we leerden er ook nieuwe mensen kennen. Deze informele momenten gaven ons de gelegenheid om meer te leren over de Oostenrijkse cultuur en om in gesprek te gaan met zowel medestudenten als lokale bewoners.
          </p>
          <p>
            Op zaterdag hadden we een vrije dag om Salzburg te verkennen. Salzburg is beroemd om zijn barokke architectuur en zijn band met de componist Mozart. We hebben de stad grondig verkend, van de mooie tuinen van Schloss Mirabell tot de indrukwekkende vesting Hohensalzburg die hoog boven de stad uittorent. Hoewel we niet naar de top van de vesting zijn gegaan was het toch indrukwekkend om deze vanuit het centrum te bewonderen. Het was een geweldige afsluiting van onze reis en gaf ons de kans om de rijke cultuur en geschiedenis van Oostenrijk verder te ontdekken.
          </p>
          <p>
            De studiereis naar Linz was voor mij een heel leerrijke uitstap. We kregen de kans om kennis te maken met de FH OÖ in Hagenberg en het Ars Electronica Center. Wat me vooral is bijgebleven is hoe technologie daar niet losstaat van kunst, samenleving en duurzaamheid.
          </p>
          <p>
            Ik heb tijdens de reis geleerd dat technologische innovatie niet alleen draait om efficiëntie en functionaliteit, maar ook om ethiek, verantwoordelijkheid en maatschappelijke impact. De interactieve rondleiding in het Ars Electronica Center heeft me op een andere manier laten nadenken over de rol van technologie in onze wereld. Ik vond het inspirerend hoe kunst en wetenschap samenwerkten om thema’s als klimaatverandering zichtbaar te maken. Dat heeft me gemotiveerd om binnen mijn eigen opleiding creatiever te denken en open te staan voor interdisciplinaire samenwerking.
          </p>
          <p>
            Een onverwacht waardevol aspect van de reis was de sociale connectie. We maakten vrienden met lokale inwoners, zowel jongeren als ouderen. We hadden gesprekken die me oprecht deden nadenken over studeren of werken in het buitenland. Ook binnen de groep was de sfeer heel positief wat zorgde voor een sterk groepsgevoel. Het voelde echt als een ervaring die we samen deelden en waar we als groep sterker uitkwamen.
          </p>
          <p>
            Echte problemen heb ik niet ervaren tijdens de reis. We konden voordelig met de tram reizen en waren ook niet bang om te wandelen wanneer dat nodig was. Al moet ik achteraf toegeven dat een uur wandelen toch vermoeiender was dan ik op voorhand had ingeschat. Dat heeft me geleerd om bij het plannen van zo'n dag net iets realistischer te zijn over afstanden en tijd. 
          </p>
        </div>
      </div>
    </div>
  </transition>
  <section
      id="final-reflection"
      class="flex flex-col items-center justify-center text-center
           h-screen bg-gradient-to-br
           text-white px-4 max-w-7xl mx-auto"
  >

  </section>
</template>

<style scoped>
  .opacity-0 {
    opacity: 0;
  }
</style>