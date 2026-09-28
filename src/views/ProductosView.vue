<script setup>
import { computed, ref } from 'vue'
import ProductoCard from '../components/ProductoCard.vue'
import { productos } from '../data/productos'

const busqueda = ref('')
const categoriaSeleccionada = ref('Todas')

const favoritos = ref(
  JSON.parse(localStorage.getItem('favoritos') || '[]')
)

const categorias = computed(() => {
  return ['Todas', ...new Set(productos.map(producto => producto.categoria))]
})

const productosFiltrados = computed(() => {
  return productos.filter(producto => {
    const coincideBusqueda =
      producto.nombre
        .toLowerCase()
        .includes(busqueda.value.toLowerCase())

    const coincideCategoria =
      categoriaSeleccionada.value === 'Todas' ||
      producto.categoria === categoriaSeleccionada.value

    return coincideBusqueda && coincideCategoria
  })
})

function cambiarFavorito(id) {
  if (favoritos.value.includes(id)) {
    favoritos.value = favoritos.value.filter(
      favoritoId => favoritoId !== id
    )
  } else {
    favoritos.value.push(id)
  }

  localStorage.setItem(
    'favoritos',
    JSON.stringify(favoritos.value)
  )
}

function esFavorito(id) {
  return favoritos.value.includes(id)
}
</script>

<template>
  <section class="pagina">
    <div class="encabezado-pagina">
      <p class="etiqueta">Feria Artesanal de Ñuble</p>

      <h1>Catálogo de productos</h1>

      <p>
        Explora productos elaborados por emprendedores y artesanos
        de distintas comunas de Ñuble.
      </p>
    </div>

    <div class="filtros">
      <div>
        <label for="busqueda">Buscar producto</label>

        <input
          id="busqueda"
          v-model="busqueda"
          type="text"
          placeholder="Escribe el nombre..."
        />
      </div>

      <div>
        <label for="categoria">Categoría</label>

        <select
          id="categoria"
          v-model="categoriaSeleccionada"
        >
          <option
            v-for="categoria in categorias"
            :key="categoria"
            :value="categoria"
          >
            {{ categoria }}
          </option>
        </select>
      </div>
    </div>

    <p class="resultado">
      {{ productosFiltrados.length }}
      producto(s) encontrado(s)
    </p>

    <div
      v-if="productosFiltrados.length > 0"
      class="productos-grid"
    >
      <ProductoCard
        v-for="producto in productosFiltrados"
        :key="producto.id"
        :producto="producto"
        :favorito="esFavorito(producto.id)"
        @cambiar-favorito="cambiarFavorito"
      />
    </div>

    <div v-else class="sin-resultados">
      <h2>No encontramos productos</h2>
      <p>
        Prueba con otro nombre o selecciona otra categoría.
      </p>
    </div>
  </section>
</template>