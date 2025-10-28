<template>
  <div class="seleccion-multiple-container">
    <h2>Selección Múltiple</h2>
    
    <div class="select-container">
      <select multiple v-model="seleccionados">
        <option :value="option" v-for="(option, i) in list" :key="i">
          {{ option }}
        </option>
      </select>
      <button @click="monstrarSeleccionados">
        {{ monstrar ? "Ocultar Seleccionados" : "Mostrar Seleccionados" }}
      </button>
    </div>

    <transition name="fade">
      <div class="list" v-if="monstrar && seleccionados.length > 0">
        <h3>Opciones seleccionadas:</h3>
        <ul>
          <li v-for="(text, i) in seleccionados" :key="i">
            {{ text }}
          </li>
        </ul>
      </div>
      <div class="list" v-else-if="monstrar">
        <h3>Ninguna opción seleccionada.</h3>
      </div>
    </transition>

    <div class="multiselect-container">
      <h3>Componente vue-multiselect</h3>
      <Multiselect
        v-model="value"
        :options="options"
        :multiple="true"
        :close-on-select="false"
        placeholder="Selecciona opciones"
      />
    </div>
  </div>
</template>

<script>
import Multiselect from "vue-multiselect";

export default {
  name: "SeleccionMultiple",
  components: { Multiselect },
  data() {
    return {
      seleccionados: [],
      list: ["Opción 1", "Opción 2", "Opción 3", "Opción 4", "Opción 5"],
      monstrar: false,
      value: [],
      options: ["Opción 1", "Opción 2", "Opción 3", "Opción 4", "Opción 5"],
    };
  },
  methods: {
    monstrarSeleccionados() {
      this.monstrar = !this.monstrar;
    },
  },
};
</script>

<style src="vue-multiselect/dist/vue-multiselect.css"></style>
<style scoped>
/* Contenedor principal */
.seleccion-multiple-container {
  max-width: 650px;
  margin: 3rem auto;
  padding: 2.5rem 2rem;
  background: linear-gradient(145deg, #fefefe, #eaeaea);
  border-radius: 16px;
  box-shadow: 0 10px 25px rgba(0, 0, 0, 0.08);
  font-family: 'Poppins', sans-serif;
  text-align: center;
  transition: all 0.3s;
}

/* Encabezados */
h2 {
  color: #1f2937;
  font-weight: 700;
  margin-bottom: 2rem;
  font-size: 2rem;
}

h3 {
  color: #374151;
  font-weight: 600;
  margin: 1.5rem 0 1rem;
}

/* Select y botón */
.select-container {
  display: flex;
  flex-direction: column;
  gap: 1.2rem;
  align-items: center;
}

select {
  width: 100%;
  max-width: 300px;
  height: 160px;
  padding: 0.6rem;
  border-radius: 12px;
  border: 1px solid #d1d5db;
  font-size: 1rem;
  transition: border-color 0.3s, box-shadow 0.3s;
  background: #ffffff;
}

select:focus {
  outline: none;
  border-color: #3b82f6;
  box-shadow: 0 0 0 4px rgba(59, 130, 246, 0.2);
}

button {
  padding: 0.8rem 2rem;
  background: #3b82f6;
  color: #fff;
  border: none;
  border-radius: 10px;
  font-weight: 600;
  cursor: pointer;
  transition: all 0.3s;
}

button:hover {
  background: #2563eb;
  transform: translateY(-2px);
  box-shadow: 0 4px 15px rgba(59, 130, 246, 0.3);
}

/* Lista de seleccionados */
.list {
  margin-top: 2rem;
  padding: 1.5rem;
  border-radius: 12px;
  background-color: #ffffff;
  border: 1px solid #e5e7eb;
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.06);
  text-align: left;
  transition: all 0.3s;
}

.list ul {
  list-style-type: none;
  padding: 0;
  margin: 0;
}

.list li {
  padding: 0.75rem 1rem;
  margin-bottom: 0.6rem;
  border-radius: 8px;
  background-color: #eff6ff;
  color: #1f2937;
  font-weight: 500;
  transition: background 0.3s;
}

.list li:hover {
  background-color: #dbeafe;
}

/* Contenedor vue-multiselect */
.multiselect-container {
  margin-top: 3rem;
  text-align: left;
}

/* Transición fade */
.fade-enter-active, .fade-leave-active {
  transition: opacity 0.5s;
}
.fade-enter, .fade-leave-to {
  opacity: 0;
}

/* Contenedor de multiselect */
:deep(.multiselect__tags) {
  border: 1px solid #cbd5e1;
  border-radius: 14px;
  background-color: #f8fafc;
  padding: 0.5rem 0.5rem;
  font-size: 1rem;
  min-height: 46px;
  transition: all 0.3s;
}

:deep(.multiselect__tags:focus-within) {
  border-color: #3b82f6;
  box-shadow: 0 0 0 4px rgba(59, 130, 246, 0.2);
}

/* Cada tag seleccionada */
:deep(.multiselect__tag) {
  background: linear-gradient(135deg, #3b82f6, #60a5fa);
  color: #fff;
  border-radius: 10px;
  font-size: 0.9rem;
  padding: 0.25rem 0.6rem;
  margin-right: 0.3rem;
  display: flex;
  align-items: center;
  transition: all 0.3s;
}

:deep(.multiselect__tag:hover) {
  background: linear-gradient(135deg, #2563eb, #3b82f6);
}

/* Icono de cerrar tag */
:deep(.multiselect__tag-icon) {
  margin-left: 4px;
  cursor: pointer;
  transition: all 0.2s;
}

:deep(.multiselect__tag-icon:hover) {
  transform: scale(1.2);
  color: #e0f2fe;
}

/* Opciones del dropdown */
:deep(.multiselect__option) {
  padding: 0.6rem 1rem;
  border-radius: 10px;
  transition: all 0.3s;
}

:deep(.multiselect__option--highlight) {
  background-color: #3b82f6;
  color: #fff;
}

:deep(.multiselect__option--selected) {
  background: #bfdbfe;
  color: #1e3a8a;
  font-weight: 600;
}

/* Input */
:deep(.multiselect__input) {
  font-size: 1rem;
  background-color: #f8fafc;
  padding: 0.5rem;
}

/* Dropdown content wrapper */
:deep(.multiselect__content-wrapper) {
  border-radius: 14px;
  border: 1px solid #cbd5e1;
  box-shadow: 0 8px 24px rgba(0, 0, 0, 0.1);
  background-color: #ffffff;
  transition: all 0.3s;
}

/* Efecto hover sobre opciones */
:deep(.multiselect__option:hover) {
  background-color: #e0f2fe;
  color: #1e3a8a;
  cursor: pointer;
}

</style>
