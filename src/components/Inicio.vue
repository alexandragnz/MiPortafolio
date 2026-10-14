<template>
  <div id="inicio"
    class="container mx-auto my-12 px-6 flex flex-col md:flex-row md:items-center justify-center gap-8 relative min-h-[250px]">

    <!-- Foto -->
    <img src="/agonzaleze.png" alt="Foto de perfil de Alexandra González"
      class="w-48 h-48 sm:w-60 sm:h-60 rounded-full object-cover shadow-md mx-auto md:mx-0 shrink-0" />

    <div class="flex flex-col text-center md:text-left mt-3 md:ml-6">

      <h1
        class="bg-gradient-to-r from-[#FFFFFF] to-[#19D0AC] bg-clip-text text-transparent text-3xl sm:text-4xl font-bold leading-tight">
        ¡Hola! <br class="hidden md:block" />
        Bienvenido/a soy Alexandra González.
      </h1>
      <span class="text-white text-xl sm:text-2xl font-afacad mt-2">
        Diseñadora de Interfaces (UI/UX) y desarrolladora Front-End.
      </span>

      <!-- Botones inicio-->
      <div
        class="flex flex-col sm:flex-row items-center gap-3 md:gap-4 w-full sm:w-auto mt-6 mx-auto md:ml-auto md:mr-0">
        <a href="#proyectos" class="btn btn-filled w-full sm:w-auto bg-[#30ADA2]">
          Proyectos
        </a>

        <!-- Btn descarga CV -->
        <a href="/DiseñadoraDesarrolladorawebAlexandra GonzalezCV.pdf" download class="btn w-full sm:w-auto">
          <img src="/descargar.png" alt="Icono de descarga" class="w-4 h-4 shrink-0 object-contain" />
          <span>Descargar CV</span>
        </a>

      </div>

    </div>
  </div>
</template>