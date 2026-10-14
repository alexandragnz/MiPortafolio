<script setup>
import { ref } from 'vue'

// Estado del formulario
const form = ref({
  nombre: '',
  email: '',
  mensaje: ''
})

const enviando = ref(false)
const mensajeEnviado = ref(false)
const errorEnvio = ref(false)


const FORMSPREE_ENDPOINT = 'https://formspree.io/f/xppwdrwb'

const handleSubmit = async () => {
  enviando.value = true
  mensajeEnviado.value = false
  errorEnvio.value = false

  try {
    const response = await fetch(FORMSPREE_ENDPOINT, {
      method: 'POST',
      headers: {
        'Content-Type': 'application/json',
        'Accept': 'application/json'
      },
      body: JSON.stringify({
        name: form.value.nombre,
        email: form.value.email,
        message: form.value.mensaje
      })
    })

    if (response.ok) {
      mensajeEnviado.value = true
      form.value = { nombre: '', email: '', mensaje: '' }

      // Ocultar mensaje de éxito tras 5 segundos
      setTimeout(() => {
        mensajeEnviado.value = false
      }, 5000)
    } else {
      errorEnvio.value = true
    }
  } catch (error) {
    errorEnvio.value = true
  } finally {
    enviando.value = false
  }
}
</script>

<template>
  <section id="contacto" class="py-16 px-6 max-w-6xl mx-auto">
    <div class="text-center max-w-2xl mx-auto mb-12">
      <h2 class="text-3xl md:text-4xl font-bold text-white mb-4">
        Hablemos de tu próximo proyecto.
      </h2>
      <p class="text-slate-300 text-base md:text-lg leading-relaxed">
        ¿Tienes una idea en mente o buscas potenciar tu presencia digital? Envíame un mensaje y nos pondremos en
        contacto a la brevedad.
      </p>
    </div>

    <!-- Layout contacto -->
    <div class="grid grid-cols-1 lg:grid-cols-12 gap-8 items-start">

      <!-- Col izquierda-->
      <div class="lg:col-span-5 bg-[#1e1e1e] rounded-2xl p-6 md:p-8 shadow-xl space-y-6">
        <h3 class="text-xl font-bold text-white mb-2">Información de contacto</h3>
        <p class="text-slate-300 text-sm leading-relaxed">
          También puedes escribirme directamente por correo o revisar mi trabajo en plataformas profesionales.
        </p>

        <div class="space-y-4 pt-2">

          <!-- Email -->
          <a href="mailto:algonzalezelgueta@gmail.com"
            class="btn-filled flex items-center gap-3 p-4 rounded-xl bg-[#262626]">
            <img src="/gmail.png" alt="Gmail" class="w-6 h-6 shrink-0" />
            <span class="text-sm text-slate-200 truncate">
              algonzalezelgueta@gmail.com
            </span>
          </a>

          <!-- LinkedIn -->
          <a href="https://www.linkedin.com/in/algonzaleze/" target="_blank" rel="noopener noreferrer"
            class="btn-filled flex items-center gap-4 p-4 rounded-xl bg-[#262626] hover:border-[#30ADA2] transition-colors group">
            <img src="/linkedin.png" alt="LinkedIn" class="w-7 h-7" />
            <div>
              <span class="text-sm font-medium text-slate-200 group-hover:text-white">Perfil de LinkedIn</span>
            </div>
          </a>

                    <!-- GitHub-->
          <a href="https://github.com/alexandragnz" target="_blank" rel="noopener noreferrer"
            class="btn-filled flex items-center gap-4 p-4 rounded-xl bg-[#262626] hover:border-[#30ADA2] transition-colors group">
            <img src="/github.png" alt="GitHub" class="w-7 h-7" />
            <div>
              <span class="text-sm font-medium text-slate-200 group-hover:text-white">Repositorio GitHub</span>
            </div>
          </a>

        </div>
      </div>

      <!-- Col derecha formulario contacto -->
      <div class="lg:col-span-7 bg-[#1e1e1e] rounded-2xl p-6 md:p-8 shadow-xl">
        <form @submit.prevent="handleSubmit" class="space-y-5">

          <div>
            <label for="nombre" class="block text-xs font-medium text-slate-300 mb-2">
              Nombre completo
            </label>
            <input id="nombre" v-model="form.nombre" type="text" required placeholder="Tu nombre"
              class="w-full px-4 py-3 rounded-xl bg-[#262626] text-white focus:outline-none focus:border-[#30ADA2] transition-colors text-sm" />
          </div>

          <div>
            <label for="email" class="block text-xs font-medium text-slate-300 mb-2">
              Correo electrónico
            </label>
            <input id="email" v-model="form.email" type="email" required placeholder="tucorreo@electronico.com"
              class="w-full px-4 py-3 rounded-xl bg-[#262626] text-white focus:outline-none focus:border-[#30ADA2] transition-colors text-sm" />
          </div>

          <div>
            <label for="mensaje" class="block text-xs font-medium text-slate-300 mb-2">
              Mensaje
            </label>
            <textarea id="mensaje" v-model="form.mensaje" rows="4" required placeholder="Cuéntame sobre tu proyecto..."
              class="w-full px-4 py-3 rounded-xl bg-[#262626] text-white focus:outline-none focus:border-[#30ADA2] transition-colors text-sm resize-none"></textarea>
          </div>

          <!-- Btn envío -->
          <button type="submit" :disabled="enviando"
            class="btn-filled w-full py-3.5 px-6 rounded-xl bg-[#30ADA2] text-white font-medium text-sm transition-all duration-300 flex items-center justify-center gap-2 disabled:opacity-50 cursor-pointer">
            <span v-if="enviando">Enviando mensaje...</span>
            <span v-else>Enviar mensaje</span>
          </button>

          <!-- Feedback Éxito -->
          <div v-if="mensajeEnviado"
            class="p-4 rounded-xl bg-[#30ADA2]/10 border border-[#30ADA2] text-[#30ADA2] text-xs font-medium text-center transition-all">
            ¡Tu mensaje ha sido enviado exitosamente! Nos pondremos en contacto pronto.
          </div>

          <!-- Feedback Error -->
          <div v-if="errorEnvio"
            class="p-4 rounded-xl bg-red-500/10 border border-red-500 text-red-400 text-xs font-medium text-center transition-all">
            Hubo un problema al enviar el mensaje. Inténtalo nuevamente o escríbeme directamente a mi correo.
          </div>

        </form>
      </div>
    </div>
  </section>
</template>