<script setup>
import { reactive } from "vue";
import Alert from "./Alert.vue";

const alert = reactive({
  type: "",
  message: "",
});

const state = reactive({
  name: "",
  email: "",
  phone: "",
  date: "",
  Symptoms: "",
});

const validate = (e) => {
  if (Object.values(state).includes("")) {
    alert.message = "Todos los campos son obligatorios";
    alert.type = "error";
    return;
  }
  console.log("Agregando");
};
</script>

<template>
  <div class="md:w-1/2">
    <h2 class="font-bold text-3xl text-center">Seguimiento de pacientes</h2>
    <p class="text-lg mt-5 text-center mb-10">
      Añade pacientes
      <span class="text-indigo-600 font-bold">Administralos</span>
    </p>

    <Alert v-if="alert.message" :alert="alert" />

    <form
      class="bg-white shadow-md rounded-lg py-10 px-5 mb-10"
      @submit.prevent="validate"
    >
      <div class="mb-5">
        <label class="block text-gray-700 uppercase font-bold" for="name">
          Nombre del paciente
        </label>
        <input
          type="text"
          id="name"
          placeholder="Nombre del paciente"
          class="border-2 w-full p-2 m-2 placeholder-gray rounded-md"
          v-model="state.name"
        />
      </div>
      <div class="mb-5">
        <label class="block text-gray-700 uppercase font-bold" for="email">
          Correo electrónico
        </label>
        <input
          type="email"
          id="email"
          placeholder="Correo electrónico"
          class="border-2 w-full p-2 m-2 placeholder-gray rounded-md"
          v-model="state.email"
        />
      </div>
      <div class="mb-5">
        <label class="block text-gray-700 uppercase font-bold" for="phone">
          Número de teléfono
        </label>
        <input
          type="tel"
          id="phone"
          placeholder="Número de teléfono"
          class="border-2 w-full p-2 m-2 placeholder-gray rounded-md"
          v-model="state.phone"
        />
      </div>
      <div class="mb-5">
        <label class="block text-gray-700 uppercase font-bold" for="date">
          Fecha de alta
        </label>
        <input
          type="date"
          id="date"
          class="border-2 w-full p-2 m-2 placeholder-gray rounded-md"
          v-model="state.date"
        />
      </div>
      <div class="mb-5">
        <label class="block text-gray-700 uppercase font-bold" for="Symptoms">
          Síntomas
        </label>
        <textarea
          id="Symptoms"
          placeholder="Describe los Síntomas del paciente"
          class="border-2 w-full p-2 m-2 placeholder-gray rounded-md h-40"
          v-model="state.Symptoms"
        />
      </div>

      <input
        type="submit"
        class="bg-indigo-600 w-full p-3 text-white uppercase font-bold hover:bg-indigo-800 cursor-pointer transition-colors"
        value="Registrar paciente"
      />
    </form>
  </div>
</template>