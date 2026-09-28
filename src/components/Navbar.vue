<script setup>
import { computed, ref } from 'vue'
import { RouterLink } from 'vue-router'

const favoritos = ref(
  JSON.parse(localStorage.getItem('favoritos') || '[]')
)

const cantidadFavoritos = computed(() => {
  return favoritos.value.length
})

window.addEventListener('storage', () => {
  favoritos.value = JSON.parse(
    localStorage.getItem('favoritos') || '[]'
  )
})
</script>

<template>
  <header class="navbar">
    <div class="marca">
      <h2>Feria Ñuble</h2>
    </div>

    <nav>
      <RouterLink to="/">Inicio</RouterLink>

      <RouterLink to="/productos">
        Productos
      </RouterLink>

      <RouterLink to="/favoritos">
        Favoritos
        <span class="contador-favoritos">
          {{ cantidadFavoritos }}
        </span>
      </RouterLink>

      <RouterLink to="/contacto">
        Contacto
      </RouterLink>
    </nav>
  </header>
</template>