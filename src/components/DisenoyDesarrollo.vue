<script setup>
import { ref } from 'vue'

const activeTab = ref('diseno')

const herramientas = [
  'GitHub', 'VSCode', 'Vercel', 'Photopea & Photoshop', 'Cloudflare', 'WordPress', 'Google Search Console', 'XAMPP Control Panel'
]

const disenoSkills = [
  'Diseño centrado en el usuario', 'Arquitectura de la información', 'Wireframing', 'Design systems', 'UX/UI', 'Prototipado interactivo', 'Figma', 'Google Fonts'
]

const desarrolloSkills = [
  'HTML/CSS', 'CSS Grid / Flexbox', 'Maquetación adaptable', 'Tailwind CSS', 'Bootstrap', 'SCSS', 'JavaScript', 'Vue.js', 'Node.js', 'PHP', 'SQL', 'API REST'
]
</script>

<template>
  <hr class="border-t border-gray-500 my-8 mx-auto w-3/4" />

  <section id="diseno-desarrollo" class="py-12 px-6 max-w-6xl mx-auto">
    <div class="text-center max-w-3xl mx-auto mb-12">
      <h2 class="mb-3">
        Diseño, desarrollo y herramientas.
      </h2>
      <p class="text-slate-300 text-base md:text-lg leading-relaxed">
        Mi proceso de trabajo se basa en 4 etapas iterativas fundamentales. Estas son descubrimiento y estrategia,
        diseño de interfaz e identidad, desarrollo Front-End, pruebas y optimización y entrega.
      </p>
    </div>

    <!-- Tarjetas -->
    <div class="grid grid-cols-1 lg:grid-cols-12 gap-8 items-start">

      <!-- Herramientas e infraestructura -->
      <div class="lg:col-span-5 relative pt-5">
        <div class="absolute -top-1 left-4 bg-[#30ADA2] text-white font-medium px-5 py-2 rounded-2xl shadow-md z-10">
          Herramientas e infraestructura
        </div>

        <div class="bg-[#1e1e1e] rounded-2xl p-6 pt-10 bshadow-xl min-h-[220px]">
          <div class="flex flex-wrap gap-2.5">
            <span v-for="item in herramientas" :key="item"
              class="px-3.5 py-1.5 rounded-full text-xs font-medium border border-slate-700 text-slate-300 bg-[#262626] hover:border-[#30ADA2] transition-colors cursor-default">
              {{ item }}
            </span>
          </div>
        </div>
      </div>

      <!-- Toggler (Diseño / Desarrollo) -->
      <div class="lg:col-span-7 relative pt-5">
        <div class="absolute -top-1 left-4 flex gap-3 z-10">
          <a @click="activeTab = 'diseno'"
            class="btn-filled px-6 py-2 rounded-2xl font-medium transition-all duration-300"
            :class="activeTab === 'diseno'
              ? 'bg-[#30ADA2] text-white shadow-md' : 'bg-[#1e1e1e] text-slate-300 border border-slate-700 hover:border-[#30ADA2]'">
            Diseño
          </a>

          <a @click="activeTab = 'desarrollo'"
            class="btn-filled px-6 py-2 rounded-2xl font-medium transition-all duration-300" :class="activeTab === 'desarrollo'
              ? 'bg-[#30ADA2] text-white shadow-md'
              : 'bg-[#1e1e1e] text-slate-300 border border-slate-700 ]'">
            Desarrollo
          </a>
        </div>

        <!-- Contenedor oscuro-->
        <div class="bg-[#1e1e1e] rounded-2xl p-6 pt-10  shadow-xl min-h-[220px]">

          <!-- Diseño -->
          <div v-if="activeTab === 'diseno'" class="flex flex-wrap gap-2.5 animate-fadeIn">
            <span v-for="skill in disenoSkills" :key="skill"
              class="px-3.5 py-1.5 rounded-full text-xs font-medium border border-slate-700 text-slate-300 bg-[#262626] hover:border-[#30ADA2] transition-colors cursor-default">
              {{ skill }}
            </span>
          </div>

          <!--  Desarrollo -->
          <div v-else class="flex flex-wrap gap-2.5 animate-fadeIn">
            <span v-for="skill in desarrolloSkills" :key="skill"
              class="px-3.5 py-1.5 rounded-full text-xs font-medium border border-slate-700 text-slate-300 bg-[#262626] hover:border-[#30ADA2] transition-colors cursor-default">
              {{ skill }}
            </span>
          </div>

        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
@keyframes fadeIn {
  from {
    opacity: 0;
    transform: translateY(4px);
  }

  to {
    opacity: 1;
    transform: translateY(0);
  }
}

.animate-fadeIn {
  animation: fadeIn 0.25s ease-in-out forwards;
}
</style>