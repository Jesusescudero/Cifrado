<template>
  <div class="app-container">
    <header>
      <h1 class="app-title">Aplicación de Cifrado Vertical</h1>
    </header>

    <!-- Sección de Instrucciones para usar los cifrados -->
    <main class="vertical-container">
      <section class="vertical-item">
        <h2>Instrucciones para usar los cifrados</h2>
        <p>
          <strong>Para el Cifrado César:</strong> Ingresa el texto que quieres cifrar y luego proporciona un número de desplazamiento. 
          Cada letra será movida en el alfabeto por el número que ingreses.
        </p>
        <p>
          <strong>Para el Cifrado Escítala:</strong> Ingresa el texto que deseas cifrar y elige cuántas columnas usar. 
          El texto se reorganizará en base a esas columnas.
        </p>
      </section>

      <!-- Sección de Cifrado César -->
      <section class="vertical-item">
        <CifradoCesar />
        <button @click="mostrarCesarExplicacion" class="btn-explicacion">
          ¿Cómo funciona el Cifrado César?
        </button>
        <!-- Usar el componente ExplicacionCifrado para mostrar la información -->
        <ExplicacionCifrado
          v-if="mostrarExplicacionCesar"
          titulo="Cifrado César"
          descripcion="El Cifrado César es un cifrado por sustitución en el cual cada letra del mensaje se desplaza un número fijo de posiciones en el alfabeto. 
                      Por ejemplo, si eliges un desplazamiento de 3, la 'A' se convierte en 'D', la 'B' en 'E', y así sucesivamente. 
                      Este cifrado es uno de los métodos más antiguos, utilizado por Julio César para enviar mensajes militares en la época romana. 
                      Sin embargo, debido a su simplicidad, puede ser fácilmente vulnerado con ataques de fuerza bruta, ya que solo existen 25 posibles claves para probar."
        />
      </section>

      <!-- Sección de Cifrado Escítala -->
      <section class="vertical-item">
        <CifradoEscitala />
        <button @click="mostrarEscitalaExplicacion" class="btn-explicacion">
          ¿Cómo funciona el Cifrado Escítala?
        </button>
        <!-- Usar el componente ExplicacionCifrado para mostrar la información -->
        <ExplicacionCifrado
          v-if="mostrarExplicacionEscitala"
          titulo="Cifrado Escítala"
          descripcion="El Cifrado Escítala es un método de cifrado por transposición que fue utilizado por los antiguos griegos. 
                      Funciona organizando el mensaje en filas y columnas, y luego leyendo el texto columna por columna para reordenarlo. 
                      En la antigüedad, se utilizaba un cilindro llamado 'escítala', en el cual se envolvía una tira de cuero con el mensaje escrito, y solo el cilindro correcto podía desenrollar el mensaje de manera legible. 
                      Aunque es más seguro que el Cifrado César para mensajes cortos, también es vulnerable si el atacante conoce la estructura de columnas utilizada para cifrar el mensaje."
        />
      </section>

      <!-- Comparación de los cifrados -->
      <section class="vertical-item">
        <h2>Comparación entre los cifrados</h2>
        <p>
          <strong>Cifrado César:</strong> Es un método simple de sustitución. Es fácil de entender pero vulnerable a ataques de fuerza bruta, ya que solo tiene 25 posibles claves.
        </p>
        <p>
          <strong>Cifrado Escítala:</strong> Es un método de transposición. Es más seguro que el Cifrado César para mensajes cortos, pero también puede ser descifrado si se conoce el número de columnas.
        </p>
        <h3>Análisis de seguridad</h3>
        <p>
          Ambos métodos son históricos y no son recomendados para proteger información en la actualidad, ya que pueden ser fácilmente quebrantados con herramientas modernas.
        </p>
        <p>
          Sin embargo, sirven para entender los principios básicos de cifrado por sustitución y transposición.
        </p>
      </section>
    </main>

    <footer>
      <p>Proyecto de Seguridad Informática - Cifrados César y Escítala</p>
    </footer>
  </div>
</template>

<script>
import CifradoCesar from './components/CifradoCesar.vue';
import CifradoEscitala from './components/CifradoEscitala.vue';
import ExplicacionCifrado from './components/ExplicacionCifrado.vue';

export default {
  components: {
    CifradoCesar,
    CifradoEscitala,
    ExplicacionCifrado,
  },
  data() {
    return {
      mostrarExplicacionCesar: false,
      mostrarExplicacionEscitala: false,
    };
  },
  methods: {
    // Alterna la visibilidad de la explicación para el Cifrado César
    mostrarCesarExplicacion() {
      this.mostrarExplicacionCesar = !this.mostrarExplicacionCesar;
    },
    // Alterna la visibilidad de la explicación para el Cifrado Escítala
    mostrarEscitalaExplicacion() {
      this.mostrarExplicacionEscitala = !this.mostrarExplicacionEscitala;
    },
  },
};
</script>

<style scoped>
.app-container {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  min-height: 100vh;
  background-color: #f3f4f6;
  font-family: 'Arial', sans-serif;
}

header {
  margin-top: 20px;
  text-align: center;
}

.app-title {
  color: #333;
  font-size: 24px;
}

.vertical-container {
  display: flex;
  flex-direction: column;
  gap: 20px;
  padding: 40px;
  max-width: 600px;
  width: 100%;
}

.vertical-item {
  background-color: #fff;
  padding: 20px;
  border-radius: 8px;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
  transition: all 0.3s ease;
}

footer {
  margin-top: 20px;
  padding: 10px;
  color: #666;
  text-align: center;
}

.btn-explicacion {
  margin-top: 10px;
  padding: 8px 15px;
  background-color: #007bff;
  color: white;
  border: none;
  border-radius: 5px;
  cursor: pointer;
}

.btn-explicacion:hover {
  background-color: #0056b3;
}

/* Media Queries para pantallas más pequeñas */
@media (max-width: 768px) {
  .app-title {
    font-size: 22px;
  }

  .vertical-container {
    padding: 20px;
  }

  .vertical-item {
    padding: 15px;
  }

  .btn-explicacion {
    padding: 8px 12px;
  }
}

/* Media Queries para pantallas muy pequeñas (teléfonos móviles) */
@media (max-width: 480px) {
  .app-title {
    font-size: 20px;
  }

  .vertical-container {
    padding: 10px;
  }

  .vertical-item {
    padding: 10px;
  }

  .btn-explicacion {
    padding: 6px 10px;
  }
}
</style>
