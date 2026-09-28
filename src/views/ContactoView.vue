<script setup>
import { ref } from 'vue'

const nombre = ref('')
const email = ref('')
const mensaje = ref('')
const enviado = ref(false)

function enviarFormulario() {
  if (
    nombre.value.trim() === '' ||
    email.value.trim() === '' ||
    mensaje.value.trim() === ''
  ) {
    alert('Por favor, completa todos los campos.')
    return
  }

  enviado.value = true

  nombre.value = ''
  email.value = ''
  mensaje.value = ''
}
</script>

<template>
  <section class="pagina">
    <div class="encabezado-pagina">
      <p class="etiqueta">Estamos para ayudarte</p>

      <h1>Contacto</h1>

      <p>
        ¿Tienes alguna consulta sobre nuestros productos?
        Escríbenos.
      </p>
    </div>

    <form
      class="formulario-contacto"
      @submit.prevent="enviarFormulario"
    >
      <div>
        <label for="nombre">Nombre</label>

        <input
          id="nombre"
          v-model="nombre"
          type="text"
          placeholder="Tu nombre"
        />
      </div>

      <div>
        <label for="email">Correo electrónico</label>

        <input
          id="email"
          v-model="email"
          type="email"
          placeholder="tu@email.com"
        />
      </div>

      <div>
        <label for="mensaje">Mensaje</label>

        <textarea
          id="mensaje"
          v-model="mensaje"
          rows="5"
          placeholder="Escribe tu mensaje..."
        ></textarea>
      </div>

      <button type="submit" class="boton-principal">
        Enviar mensaje
      </button>
    </form>

    <div v-if="enviado" class="mensaje-exito">
      <h2>¡Mensaje enviado!</h2>
      <p>
        Gracias por contactarnos. Hemos recibido tu mensaje.
      </p>
    </div>
  </section>
</template>