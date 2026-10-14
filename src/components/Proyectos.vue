<template>
  <hr class="border-t border-gray-500 mx-auto w-3/4" />
  <div id="proyectos" class="container mx-auto flex flex-col my-12 ">
    <h2 class="mx-auto mb-3 ">Proyectos relevantes.</h2>
    <p class="mx-5 md:mx-auto text-justify ">Como profesional he tenido la posibilidad de llevar a cabo el desarrollo
      web integral de proyectos de servicios, desde la conceptualización visual hasta la implementación técnica en
      código y SEO. Mi trabajo combina la creación de guías de estilo e identidad de marca con la construcción de
      interfaces flexibles, responsivas y optimizada usando CSS moderno y metodologías ágiles.
      Externo al mundo de las TI cuento con experiencia en otros rubros, donde he logrado desarrollar la capacidad de
      trabajar en equipo, la atención al detalle, el ser autodidacta y la comunicación efectiva, siempre motivada por la
      proactividad.
    </p>
  </div>
  <section class=" px-6 max-w-6xl mx-auto">

    <div class="">
      <!-- Bucle de Proyectos -->
      <div v-for="item in proyectos" :key="item.id" id=""
        class="grid grid-cols-1 lg:grid-cols-12 gap-8 items-center py-8">

        <!-- Col Izquierda-->
        <div class="lg:col-span-5 text-slate-200">
          <h3 class="text-2xl md:text-3xl font-bold text-white mb-3">
            {{ item.title }}
          </h3>
          <p class="text-slate-300 text-sm md:text-base leading-relaxed mb-4">
            {{ item.description }}
          </p>

          <ul class="space-y-2 text-slate-300 text-xs md:text-sm list-disc pl-5">
            <li v-for="(feature, idx) in item.features" :key="idx">
              {{ feature }}
            </li>
          </ul>
        </div>

        <!-- Col Derecha -->
        <div class="lg:col-span-7 relative flex justify-center items-center py-6">

          <!-- Pantalla figma -->
          <div @click="openGallery(item, 0)"
            class="project-mockup-bg group max-h-[250px] sm:max-h-[320px] lg:max-h-[420px] overflow-hidden rounded-xl">
            <img :src="item.mockupFigma" :alt="item.title" class="w-full h-full object-cover object-top" />
            <div class="mockup-overlay"><img src="/lupa.png" class="h-10 w-10"> Click para ampliar</div>
          </div>

          <!-- Pantalla laptop-->
          <div @click="openGallery(item, 1)"
            class="project-mockup-fg group max-h-[220px] sm:max-h-[280px] lg:max-h-[380px] overflow-hidden rounded-xl">
            <img :src="item.mockupLaptop" :alt="item.title" class="w-full h-full object-cover object-top" />
            <div class="mockup-overlay"><img src="/lupa.png" class="h-5 w-5"> Ver Galería</div>
          </div>

        </div>
      </div>
    </div>

  </section>

  <!-- Modal galería  -->
  <Teleport to="body">
    <Transition name="fade">
      <div v-if="isGalleryOpen"
        class="fixed inset-0 z-50 bg-black/90 backdrop-blur-md flex items-center justify-center p-3 sm:p-6 md:p-8"
        @click.self="closeGallery">

        <!-- Btn cerrar -->
        <button @click="closeGallery"
          class="absolute top-4 right-4 sm:top-6 sm:right-6 text-white text-2xl sm:text-3xl font-bold hover:text-[#30ADA2] transition-colors z-50 p-2">
          ✕
        </button>

        <!-- Contenedor galería -->
        <div class="relative max-w-5xl w-full flex flex-col items-center">

          <!-- Título del proyecto en el Modal -->
          <h4 class="text-white text-lg sm:text-xl md:text-2xl font-bold mb-3 sm:mb-4 text-center">
            {{ selectedProject?.title }}
          </h4>

          <!-- Visualizador de Imagen -->
          <div class="relative w-full flex items-center justify-center overflow-hidden rounded-lg">
            <img :src="selectedProject?.gallery[currentImageIndex]"
              class="max-h-[55vh] sm:max-h-[65vh] md:max-h-[75vh] max-w-full object-contain rounded-lg shadow-2xl transition-all duration-300" />

            <!-- Controles de Navegación -->
            <button @click="prevImage"
              class="absolute left-1 sm:left-4 top-1/2 -translate-y-1/2 bg-black/60 hover:bg-[#30ADA2] text-white p-2.5 sm:p-3 rounded-full transition-colors">
              ❮
            </button>
            <button @click="nextImage"
              class="absolute right-1 sm:right-4 top-1/2 -translate-y-1/2 bg-black/60 hover:bg-[#30ADA2] text-white p-2.5 sm:p-3 rounded-full transition-colors">
              ❯
            </button>
          </div>

          <!-- Indicadores-->
          <div class="flex gap-2.5 sm:gap-3 mt-4 sm:mt-6">
            <span v-for="(img, idx) in selectedProject?.gallery" :key="idx" @click="currentImageIndex = idx"
              class="w-2.5 h-2.5 sm:w-3 sm:h-3 rounded-full cursor-pointer transition-all"
              :class="currentImageIndex === idx ? 'bg-[#30ADA2] scale-125' : 'bg-slate-600'"></span>
          </div>
        </div>
      </div>
    </Transition>
  </Teleport>
</template>
<script setup>
import { ref } from 'vue'

// Estado modal
const isGalleryOpen = ref(false)
const selectedProject = ref(null)
const currentImageIndex = ref(0)

// Datos de los proyectos
const proyectos = [
  {
    id: 'anggy-costuras',
    title: 'Anggy Costuras',
    description: 'Taller de alta costura y sastrería en Santiago. Desarrollo de sitio web corporativo enfocado en la presencia digital, optimización SEO y captación de clientes.',
    features: [
      'Diseño e ilustración del imagotipo corporativo.',
      'Diseño de interfaces interactivas y prototipado en Figma.',
      'Desarrollo front-end con Vue.js 3, Tailwind CSS y Vite.',
      'Control de versiones colaborativo con Git y GitHub.',
      'Despliegue continuo en Vercel para optimización de rendimiento y SEO.'
    ],
    mockupFigma: '/anggy-figma.png',
    mockupLaptop: '/prototipoAnggy.png',
    gallery: [
      '/mockups-gallery/anggy-inicio-desk.png',
      '/mockups-gallery/anggy-inicio-2.png',
      '/mockups-gallery/anggy-inicio-mobile.png',
      '/mockups-gallery/anggy-nosotros-desk.png',
      '/mockups-gallery/anggy-nosotros-mobile.png',
      '/mockups-gallery/anggy-servicios-desk.png',
      '/mockups-gallery/anggy-servicios-mobile.png',
      '/mockups-gallery/anggy-contacto.png',
      '/mockups-gallery/anggy-contacto-mobile.png',
      '/mockups-gallery/anggy-footer-mobile.webp',
      '/mockups-gallery/anggylogo.webp'
    ]
  },
  {
    id: 'cuidamos-de-ti',
    title: 'Cuidamos de ti Chile.',
    description: 'Una agrupación de enfermeras de Santiago busca profesionalizar su marca, obtener un mayor alcance, y dar a conocer la información de la empresa.',
    features: [
      'Moodboard, diseño y guía de estilos con Figma.',
      'Desarrollo con WordPress Gutenberg.',
      'Plugins para sliders y JoinChat.'
    ],
    mockupFigma: '/cuidamosDeTiFigma.png',
    mockupLaptop: '/cuidamosdetiPrototipo.png',
    gallery: [
      '/mockups-gallery/Cuidamos-inicio-desk.png',
      '/mockups-gallery/Cuidamos-inicio-mobile.png',
      '/mockups-gallery/Cuidamos-servicios-desk.png',
      '/mockups-gallery/Cuidamos-servicios-mobile.png',
      '/mockups-gallery/Cuidamos-contacto-desk.png',
      '/mockups-gallery/Cuidamos-contacto-mobile.png',
      '/mockups-gallery/Cuidamos-nosotros.png',

    ]
  },
  {
    id: 'ssb-muebles',
    title: 'SSB Muebles a medida.',
    description: 'Este proyecto nace ante la necesidad de optimizar las cotizaciones del emprendedor.',
    features: [
      'Moodboard, diseño del sitio y guía de estilos con Figma.',
      'Desarrollo local del tema para WordPress bajo metodología BEM.',
      'Para front end Node.js, Bootstrap, Sass y JS.',
      'Control de versiones con GitHub.',
      'Plugins WordPress JoinChat y SMTP mail.'
    ],
    mockupFigma: '/SSBFigma.png',
    mockupLaptop: '/SSBPrototipo.png',
    gallery: [
      '/mockups-gallery/SSB-inicio-desk.png',
      '/mockups-gallery/SSB-inicio-mobile.png',
      '/mockups-gallery/SSB-Nosotros.png',
      '/mockups-gallery/SSB-category.png',
      '/mockups-gallery/SSB-proyectos-desk.png',
      '/mockups-gallery/SSB-proyectos-mobile.png',
      '/mockups-gallery/SSB-single.png',
      '/mockups-gallery/SSB-single-mobile.png',
      '/mockups-gallery/SSB-contacto.png',
      '/mockups-gallery/SSB-contacto-moble.png',
    ]
  }
]

//Navegación por teclado
const handleKeydown = (e) => {
  if (!isGalleryOpen.value) return

  if (e.key === 'ArrowRight') {
    nextImage()
  } else if (e.key === 'ArrowLeft') {
    prevImage()
  } else if (e.key === 'Escape') {
    closeGallery()
  }
}

// Funciones galería
const openGallery = (proyecto, index = 0) => {
  selectedProject.value = proyecto
  currentImageIndex.value = index
  isGalleryOpen.value = true
  document.body.style.overflow = 'hidden'
  window.addEventListener('keydown', handleKeydown)
}

const closeGallery = () => {
  isGalleryOpen.value = false
  document.body.style.overflow = 'auto'
  window.removeEventListener('keydown', handleKeydown)
}


const nextImage = () => {
  if (!selectedProject.value) return
  currentImageIndex.value = (currentImageIndex.value + 1) % selectedProject.value.gallery.length
}

const prevImage = () => {
  if (!selectedProject.value) return
  currentImageIndex.value = (currentImageIndex.value - 1 + selectedProject.value.gallery.length) % selectedProject.value.gallery.length
}
</script>