<script setup>
import { computed, ref } from 'vue'
import ProductoCard from '../components/ProductoCard.vue'
import { productos } from '../data/productos'

const favoritos = ref(
  JSON.parse(localStorage.getItem('favoritos') || '[]')
)

const productosFavoritos = computed(() => {
  return productos.filter(producto =>
    favoritos.value.includes(producto.id)
  )
})

function quitarFavorito(id) {
  favoritos.value = favoritos.value.filter(
    favoritoId => favoritoId !== id
  )

  localStorage.setItem(
    'favoritos',
    JSON.stringify(favoritos.value)
  )
}
</script>

<template>
  <section class="pagina">
    <div class="encabezado-pagina">
      <p class="etiqueta">Mis productos</p>

      <h1>Mis favoritos</h1>

      <p>
        Aquí puedes encontrar los productos que has guardado
        como favoritos.
      </p>
    </div>

    <div
      v-if="productosFavoritos.length > 0"
      class="productos-grid"
    >
      <ProductoCard
        v-for="producto in productosFavoritos"
        :key="producto.id"
        :producto="producto"
        :favorito="true"
        @cambiar-favorito="quitarFavorito"
      />
    </div>

    <div v-else class="sin-resultados">
      <h2>Aún no tienes favoritos</h2>

      <p>
        Ve al catálogo y agrega algunos productos a tu lista.
      </p>
    </div>
  </section>
</template>