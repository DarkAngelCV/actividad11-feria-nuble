# Feria Artesanal de Ñuble – Actividad 11

## Descripción del proyecto

Este proyecto corresponde al desarrollo de una aplicación web tipo **SPA (Single Page Application)** para la Feria Artesanal de Ñuble. La aplicación tiene como propósito presentar un catálogo de productos elaborados por emprendedores y artesanos de distintas comunas de la Región de Ñuble.

En esta actividad se amplió la aplicación desarrollada anteriormente, incorporando **Vue Router** para organizar la navegación entre diferentes vistas, rutas dinámicas para consultar información específica de cada producto, componentes reutilizables y un sistema de favoritos con persistencia mediante `localStorage`.

La aplicación permite al usuario recorrer el catálogo, buscar productos, filtrarlos por categoría, consultar el detalle de un producto, guardar productos como favoritos y comunicarse mediante un formulario de contacto.

## Objetivos

* Implementar una aplicación SPA utilizando Vue 3.
* Incorporar Vue Router para gestionar la navegación entre vistas.
* Utilizar rutas dinámicas para mostrar el detalle de los productos.
* Crear componentes reutilizables para mejorar la organización del proyecto.
* Implementar un sistema de favoritos utilizando `localStorage`.
* Aplicar conceptos fundamentales de Vue como `v-model`, `v-if`, `v-for`, `computed` y `props`.
* Incorporar una página para rutas no encontradas.
* Aplicar un diseño responsive y organizado.
* Documentar y verificar el funcionamiento de la aplicación.

## Tecnologías utilizadas

* **Vue 3**
* **Vite**
* **Vue Router**
* **JavaScript**
* **HTML5**
* **CSS3**
* **LocalStorage**


## Funcionalidades implementadas

### Catálogo de productos

La vista de productos presenta un conjunto de productos artesanales de Ñuble, mostrando información como nombre, categoría, comuna, precio y descripción.

### Búsqueda y filtrado

El usuario puede buscar productos por nombre y seleccionar una categoría para reducir los resultados mostrados en el catálogo.

### Detalle dinámico

Cada producto posee una ruta dinámica utilizando su identificador.

Por ejemplo:

```text
/productos/1
```

La aplicación obtiene el identificador desde la URL y muestra la información correspondiente al producto seleccionado.

### Sistema de favoritos

El usuario puede agregar o eliminar productos de su lista de favoritos. La información se almacena mediante `localStorage`, permitiendo conservar los favoritos aunque la página sea recargada.

Además, se incorporó un contador visible en la barra de navegación que muestra la cantidad de productos favoritos.

### Formulario de contacto

La aplicación incluye un formulario donde el usuario puede ingresar su nombre, correo electrónico y mensaje.

Antes de enviar el formulario se verifica que los campos obligatorios estén completos.

### Página 404

Se incorporó una vista para informar al usuario cuando intenta acceder a una dirección que no corresponde a ninguna de las rutas disponibles.

## Componentes reutilizables

Uno de los componentes principales es `ProductoCard.vue`, utilizado para representar cada producto dentro del catálogo y también dentro de la vista de favoritos.

El componente recibe información mediante `props` y permite comunicar acciones al componente principal mediante eventos personalizados.

El componente `Navbar.vue` se utiliza de forma global para mantener la navegación disponible en las diferentes v
