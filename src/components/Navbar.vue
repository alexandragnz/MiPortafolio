<template>
  <nav class="w-full mx-auto flex items-center justify-between py-4 px-6 gap-5">
    <a href="/" id="miportafolio" class="text-[#BFBFBF] flex">
      MiPortafolio <span class="text-[#30ADA2]">Algonzaleze</span>
    </a>
    <ul class="hidden md:flex items-center gap-6">
      <li>
        <a href="#inicio"
          class="text-md font-semibold text-[#30ADA2] relative py-1 after:content-[''] after:absolute after:bottom-0 after:left-0 after:w-full after:h-[2px] after:bg-[#30ADA2] hover:text-[#97d8d3]">
          Inicio
        </a>
      </li>

      <li>
        <a href="#sobre-mi" class="text-md font-medium text-slate-300 hover:text-[#97d8d3] transition-colors py-1">
          Sobre mi
        </a>
      </li>
      <li>
        <a href="#diseno-desarrollo"
          class="text-md font-medium text-slate-300 hover:text-[#97d8d3] transition-colors py-1">
          Diseño y desarrollo
        </a>
      </li>
      <li>
        <a href="#proyectos" class="text-md font-medium text-slate-300 hover:text-[#97d8d3] transition-colors py-1">
          Proyectos
        </a>
      </li>

      <!-- Botón Destacado de Contacto -->
      <li class="ml-2">
        <a href="#contacto" class=" text-md font-medium text-slate-300 hover:text-[#97d8d3] transition-colors py-1">
          Contacto
        </a>
      </li>
    </ul>
    <!--Btn hamburguesa-->
    <button @click="toggleMenu" class="block md:hidden text-gray-500 focus:outline-none" aria-label="Abrir menú">
      <svg class="w-8 h-8" fill="none" stroke="currentColor" viewBox="0 0 24 24">
        <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 6h16M4 12h16M4 18h16"></path>
      </svg>
    </button>
  </nav>
  <!--Fondo overlay-->
  <div v-if="isOpen" @click="closeMenu" class="fixed inset-0 bg-black/50 z-50 transition-opacity md:hidden"></div>
  <aside
    class="fixed top-0 right-0 w-64 h-full bg-white z-50 shadow-xl transform transition-transform duration-300 ease-in-out md:hidden flex flex-col justify-between p-6"
    :class="isOpen ? 'translate-x-0' : 'translate-x-full'">
    <div>
      <!-- Encabezado del Offcanvas -->
      <div class="flex items-center justify-between pb-4 border-b border-gray-100">
        <span class="font-bold text-[#30ADA2]">Menú</span>
        <button @click="closeMenu" class="text-gray-500 hover:text-gray-800" aria-label="Cerrar menú">
          <svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24">
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12"></path>
          </svg>
        </button>
      </div>

      <!-- Navegación Móvil -->
      <ul class="flex flex-col gap-4 mt-6">
        <li>
          <a href="#inicio" @click="closeMenu"
            class="block text-gray-700 font-medium hover:text-[#30ADA2] transition-colors">Inicio</a>
        </li>
        <li>
          <a href="#sobre-mi" @click="closeMenu"
            class="block text-gray-700 font-medium hover:text-[#30ADA2] transition-colors">Sobre mí</a>
        </li>
        <li>
          <a href="#diseno-desarrollo" @click="closeMenu"
            class="block text-gray-700 font-medium hover:text-[#30ADA2] transition-colors">Diseño y desarrollo</a>
        </li>
        <li>
          <a href="#proyectos" @click="closeMenu"
            class="block text-gray-700 font-medium hover:text-[#30ADA2] transition-colors">Proyectos</a>
        </li>
        <li>
          <a href="#contacto" @click="closeMenu"
            class="block text-gray-700 font-medium hover:text-[#30ADA2] transition-colors">Contacto</a>
        </li>
      </ul>
    </div>
  </aside>
</template>
<script setup>
import { ref } from 'vue'

// Control de visibilidad offcanvas
const isOpen = ref(false)

const toggleMenu = () => {
  isOpen.value = !isOpen.value
}

const closeMenu = () => {
  isOpen.value = false
}
</script>