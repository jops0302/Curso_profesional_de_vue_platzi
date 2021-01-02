<template>
  <div>
    <h1>Este es un component hijo</h1>
  </div>
</template>

<script>
// Se crea el objeto vue (todos los componentes devuelven un objeto)
export default {
  data () {
    return {
      person: {
        name: 'carlos'
      }
    }
  },

  created () {
    console.log('crated...')
  },
  mounted () {
    console.log('mounted...')
  }
}
</script>

// Entonces para mostrar información cargada de un Web service al iniciar la vista, es mejor hacer la petición http en el created, ya que para cuando el mounted carga el DOM, la información ya está lista y de esa forma ganamos tiempo 😃 .

// Si, totalmente. El hook created es ideal para este tipo de casos. Gracias por el aporte!

// beforeCreate: se ejecuta justo después de la inicialización de la instancia.
// created: se ejecuta cuando la instancia y los eventos, las computed properties, el data y los métodos están creados. Normalmente se utiliza para inicializar propiedades del objeto data con consultas HTTP Get.
// beforeMount: se ejecuta justo antes de que se añada al DOM.
// mounted: se ejecuta después de añadirlo al DOM. Se puede utilizar para inicializar librerías que dependan del DOM.
// beforeUpdate: se ejecuta cuando el data cambia, pero el DOM aun no ha plasmado los cambios.
// updated: se ejecuta después de que el data cambie y el DOM muestre estos cambios.
// beforeDestroy: se ejecuta justo antes de eliminar la instancia.
// destroyed: se ejecuta cuando la instancia, los eventos, directivas e hijos del componente se han eliminado.
