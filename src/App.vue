<template>
  <div class="mx-auto container mt-5">
    <div class="conteudo p-5 shadow">
      <h1>Sobre o profissional</h1>
      <h2>Dados do profissional</h2>

      <!-- <PageOne /> -->
      <!-- <PageTwo /> -->
      <!-- <PageThree /> -->
      <PageFour />
    </div>
  </div>
</template>

<script>
// import PageOne from "./components/PageOne.vue";
// import PageTwo from "./components/PageTwo.vue";

// import PageThree from "./components/PageThree.vue";
import PageFour from "./components/PageFour.vue";
export default {
  name: "App",
  components: {
    // PageOne,
    // PageTwo,
    PageFour,
  },
};
</script>

<style>
body {
  background-color: var(--cta-1);
}
:root {
  --primary-0: #483698;
  --secondary-0: #ffffff;
  --secondary-1: #f9f9f9;
  --secondary-4: #8a8a8a;
  --secondary-7: #282828;
  --danger: #dc3545;
  --cta-1: #ffe766;
  --cta-0: #f8de40;
}

.conteudo {
  background-color: var(--secondary-0);
  border-radius: 25px;
}

.form-group {
  margin-bottom: 15px;
}

.btn-rounded {
  border-radius: 15px;
  /* background-color: var(--primary-0); */
}

/* font-family: 'Comfortaa', cursive; */
/* font-family: 'Open Sans', sans-serif; */
h1 {
  font-family: "Comfortaa", cursive;
  font-weight: bold;
  color: var(--primary-0);
}
</style>
