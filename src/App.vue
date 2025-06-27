<template>
  <div class="min-h-screen bg-gradient-to-br from-gray-900 to-gray-800 text-white p-8">
    <h1 class="text-4xl font-bold mb-8 text-center">Dronovi + computer vision ideje</h1>

<div class="bg-gray-800 p-6 rounded-2xl shadow-lg max-w-5xl mx-auto">
      <h2 class="text-3xl font-bold mb-4"> Moguće tehnologije za implementaciju CV-a</h2>
      <ul class="list-disc pl-6 space-y-2">
        <li><span class="font-semibold">CLIP</span> – Generalno prepoznavanje objekata i koncepata iz slike + teksta => (ne treba nikakav fine-tuning. Radi odlično odmah)</li>
        <li><span class="font-semibold">X-CLIP</span> – Video obrada s vremenskim kontekstom (pokreti, ponašanja) => (ne treba nikakav fine-tuning. Radi odlično odmah)</li>
        <li><span class="font-semibold">YOLOv5/v8</span> – Real-time detekcija ljudi, vozila, otpada, požara... => (može ga se dodatno fine-tunirati na custom podatke)</li>
        <li><span class="font-semibold">DeepFace / InsightFace</span> – Prepoznavanje i analiza lica => (ne treba nikakav fine-tuning. Ima ugrađene brojne mogućnosti za analizu lica)</li>
        <li><span class="font-semibold">Custom trenirani modeli</span> – Posebne CNN mreže za specifične objekte => (treniranje modela from scratch. Ukoliko nema adekvatnog modela za pojedini use-case)</li>
        <li><span class="font-semibold">Segmentation modeli (Mask R-CNN, U-Net)</span> – Precizna lokalizacija oblika => (odlični, brzi i efikasni, uklanjaju nepotrebne pozadine i ostale elemente koji narušavaju kvalitetu u svega nekoliko sekundi)</li>
        <li><span class="font-semibold">GPS + Geolokacija</span> – Pozicioniranje promatranih pojava u prostorni kontekst => (samo ubacimo neki API i trebalo bi biti OK)</li>
        <li><span class="font-semibold">OpenCV</span> – Generalna computer vision biblioteka => (omogućava obradu podataka iz kamere)</li>
        
      </ul>
    </div>

    <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-6">
      <div
        v-for="(idea, index) in ideas"
        :key="index"
        @click="selectIdea(idea)"
        class="cursor-pointer bg-gray-700 hover:bg-gray-600 p-6 rounded-2xl shadow-lg transition-all"
      >
        <h2 class="text-xl font-semibold mb-2">{{ idea.title }}</h2>
        <p class="text-gray-300">{{ idea.category }}</p>
      </div>
    </div>

    <div v-if="selectedIdea" class="fixed inset-0 bg-black bg-opacity-80 flex items-center justify-center z-50">
      <div class="bg-gray-900 rounded-2xl shadow-2xl p-8 max-w-2xl w-full relative">
        <button
          @click="selectedIdea = null"
          class="absolute top-4 right-4 text-white hover:text-red-400 text-2xl"
        >
          &times;
        </button>
        <h2 class="text-3xl font-bold mb-4">{{ selectedIdea.title }}</h2>
        <p class="text-gray-400 mb-2 italic">{{ selectedIdea.category }}</p>
        <p class="text-gray-200 leading-relaxed whitespace-pre-line">{{ selectedIdea.details }}</p>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      selectedIdea: null,
      ideas: [
        {
  title: "Detekcija požara iz zraka",
  category: "Ekologija / Spašavanje",
  details: "Dron prepoznaje vatru ispod sebe i automatski alarmira 193 i najbližu postaju."
},

  {
    title: "Inspekcija krovova i zgrada",
    category: "Industrija / Nadzor",
    details: "Otkrivanje oštećenja na fasadama, krovovima i konstrukcijama pomoću drona i CV-a."
  },
  {
    title: "Detekcija bolesti biljaka",
    category: "Poljoprivreda",
    details: "Analiza lišća radi otkrivanja bolesti na usjevima ili voćkama."
  },
  {
    title: "Pametni patrolni dron",
    category: "Sigurnost",
    details: "Automatski nadzor imanja i objekata s prepoznavanjem ljudi i vozila."
  },
  {
    title: "Detekcija ilegalnog otpada",
    category: "Ekologija",
    details: "Prepoznavanje otpada u prirodi (gume, plastika, stari uređaji) iz zraka."
  },
  {
    title: "Traženje nestalih osoba",
    category: "Spašavanje",
    details: "Pretraga terena dronom i termalnom kamerom za pronalazak ljudi."
  },
  {
    title: "Brojanje ljudi na događanjima",
    category: "Komercijalno",
    details: "Zračna analiza broja posjetitelja na eventima ili javnim skupovima."
  },
  {
  title: "Automatsko brojanje parkiranih vozila",
  category: "Komercijalno / Promet",
  details: "Praćenje zauzetosti parkirališta u realnom vremenu."
},
{
  title: "Prepoznavanje i brojanje ptica (primjenjivo i na druge životinjske vrste)",
  category: "Ekologija",
  details: "Praćenje brojnosti i migracija ptica radi zaštite vrsta."
},
{
  title: "Detekcija nepropisno parkiranih vozila",
  category: "Promet / Sigurnost",
  details: "Prepoznavanje vozila koja blokiraju promet ili pješačke prijelaze."
},
{
  title: "Automatska inspekcija željezničkih pruga",
  category: "Industrija / Transport",
  details: "Detekcija oštećenja i prepreka na prugama."
},
{
  title: "Detekcija zagađenja vodenih površina",
  category: "Ekologija",
  details: "Prepoznavanje naftnih mrlja i drugih zagađivača iz zraka."
},
{
  title: "Pregled visokih skladišnih polica",
  category: "Logistika",
  details: "Brza kontrola stanja robe i police na velikim visinama."
},
{
  title: "Inspekcija kipova i spomenika",
  category: "Kulturna baština",
  details: "Fotografira teško dostupne dijelove spomenika za restauraciju."
},
{
  title: "Pregled reflektora i rasvjete na stadionima",
  category: "Sportska infrastruktura",
  details: "Provjera stanja reflektora na visokoj poziciji bez montažnih dizalica."
},
  {
    title: "Drone + CV as a service",
    category: "Tehnički proizvod",
    details: "Snimanje određenog područja + custom analiza podataka ovisno što klijent želi"
  }
]

    }
  },
  methods: {
    selectIdea(idea) {
      this.selectedIdea = idea;
    }
  }
}
</script>

<style scoped>
body {
  font-family: 'Segoe UI', sans-serif;
}
</style>