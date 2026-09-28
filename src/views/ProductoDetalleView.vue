<script setup>
import { computed } from 'vue'
import { RouterLink, useRoute } from 'vue-router'
import { productos } from '../data/productos'

const route = useRoute()

const producto = computed(() => {
  return productos.find(
    producto => producto.id === Number(route.params.id)
  )
})
</script>

<template>
  <section class="pagina">
    <div v-if="producto" class="detalle-producto">
      <div class="detalle-imagen">
        <img
          :src="producto.imagen"
          :alt="producto.nombre"
        />
      </div>

      <div class="detalle-contenido">
        <span class="categoria">
          {{ producto.categoria }}
        </span>

        <h1>{{ producto.nombre }}</h1>

        <p class="comuna">
          📍 {{ producto.comuna }}
        </p>

        <p>
          {{ producto.descripcion }}
        </p>

        <strong class="precio">
          ${{ producto.precio.toLocaleString('es-CL') }}
        </strong>

        <RouterLink
          to="/productos"
          class="boton-principal"
        >
          Volver al catálogo
        </RouterLink>
      </div>
    </div>

    <div v-else class="sin-resultados">
      <h1>Producto no encontrado</h1>

      <p>
        El producto que buscas no existe en nuestro catálogo.
      </p>

      <RouterLink to="/productos">
        Volver a productos
      </RouterLink>
    </div>
  </section>
</template>