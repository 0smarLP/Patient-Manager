<script setup>
import { ref, reactive } from "vue";
import Header from "./components/Header.vue";
import Form from "./components/Form.vue";

const patients = ref([]);

const state = reactive({
  name: "",
  email: "",
  phone: "",
  date: "",
  symptoms: "",
});

const savePatient = () => {
  patients.value.push(state);
  console.log(patients.value);
};
</script>

<template>
  <div class="container mx-auto mt-20">
    <Header />
    <div class="mt-12 md:flex">
      <Form
        v-model:name="state.name"
        v-model:email="state.email"
        v-model:phone="state.phone"
        v-model:date="state.date"
        v-model:symptoms="state.symptoms"
        @save-patient="savePatient"
      />
      <div class="md:w-1/2 md:h-screen overflow-y-scroll">
        <h3 class="font-black text-3xl text-center">
          Administra tus Pacientes
        </h3>
        <div v-if="patients > 0"></div>
        <p v-else class="mt-20 text-2xl text-center">No hay pacientes</p>
      </div>
    </div>
  </div>
</template>

