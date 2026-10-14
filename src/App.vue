<script setup>
import { onMounted } from 'vue'
import Navbar from './components/Navbar.vue'
import Footer from './components/Footer.vue'
import Inicio from './components/Inicio.vue'
import SobreMi from './components/SobreMi.vue'
import DisenoyDesarrollo from './components/DisenoyDesarrollo.vue'
import Proyectos from './components/Proyectos.vue'
import Contacto from './components/Contacto.vue'

const navItems = [
  { name: 'Inicio', href: '#inicio' },
  { name: 'Sobre mí', href: '#sobre-mi' },
  { name: 'Diseño y desarrollo', href: '#diseno-y-desarrollo' },
  { name: 'Proyectos', href: '#proyectos' },
  { name: 'Contacto', href: '#contacto' },
]

// Animación de secciones al hacer scroll
onMounted(() => {
  const observer = new IntersectionObserver(
    (entries) => {
      entries.forEach((entry) => {
        if (entry.isIntersecting) {
          entry.target.classList.add('opacity-100', 'translate-y-0')
          entry.target.classList.remove('opacity-0', 'translate-y-10')
        }
      })
    },
    { threshold: 0.15 } // Activación cuando al 15% de visibilidad
  )

  document.querySelectorAll('.section-transition').forEach((el) => {
    observer.observe(el)
  })
})
</script>

<template>
  <div class="mx-auto bg-global min-h-screen">
    <header>
      <Navbar />
    </header>

    <main class="md:w-3/4 mx-auto">
      <section class="section-transition transition-all duration-700 ease-out opacity-0 translate-y-10">
        <Inicio />
      </section>

      <section class="section-transition transition-all duration-700 ease-out opacity-0 translate-y-10">
        <SobreMi />
      </section>

      <section class="section-transition transition-all duration-700 ease-out opacity-0 translate-y-10">
        <DisenoyDesarrollo />
      </section>

      <section class="section-transition transition-all duration-700 ease-out opacity-0 translate-y-10">
        <Proyectos />
      </section>

      <section class="section-transition transition-all duration-700 ease-out opacity-0 translate-y-10">
        <Contacto />
      </section>
    </main>

    <Footer />
  </div>
</template>