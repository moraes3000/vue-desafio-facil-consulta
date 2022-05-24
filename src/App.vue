<template>
  <div class="mx-auto container mt-5">
    <a
      type="button"
      @click.prevent="backStep({ activePhase })"
      class="btn-back"
      v-if="activePhase != 1"
    >
      <img src="img/chevron-left-solid.svg" width="15" />
    </a>

    <div class="conteudo p-5 shadow">
      <h1>Sobre o profissional</h1>
      <h2>Dados do profissional</h2>

      <div v-if="activePhase == 1">
        <PageOne />
        <div class="row">
          <div class="col-md-6">
            <button
              type="button"
              @click.prevent="goToStep(2)"
              class="btn btn-primary w-100 btn-rounded"
            >
              Proximo
            </button>
          </div>
        </div>
      </div>

      <div v-if="activePhase == 2">
        <PageTwo />
        <div class="row">
          <div class="col-md-6">
            <button
              type="button"
              @click.prevent="goToStep(3)"
              class="btn btn-primary w-100 btn-rounded"
            >
              Proximo
            </button>
          </div>
        </div>
      </div>

      <div v-if="activePhase == 3">
        <PageThree />
        <div class="row">
          <div class="col-md-6">
            <button
              type="button"
              @click.prevent="goToStep(4)"
              class="btn btn-primary w-100 btn-rounded"
            >
              Proximo
            </button>
          </div>
        </div>
      </div>

      <div v-if="activePhase == 4">
        <PageFour />
        <div class="row">
          <div class="col-md-6">
            <button
              type="button"
              @click.prevent="goToStep(4)"
              class="btn btn-primary w-100 btn-rounded"
            >
              Proximo
            </button>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import PageOne from "./components/PageOne.vue";
import PageTwo from "./components/PageTwo.vue";
import PageThree from "./components/PageThree.vue";
import PageFour from "./components/PageFour.vue";

export default {
  name: "App",
  components: {
    PageOne,
    PageTwo,
    PageThree,
    PageFour,
  },
  data: function () {
    return {
      activePhase: 1,
      nome: "",
    };
  },

  methods: {
    goToStep: function (step) {
      this.activePhase = step;
      console.log(this.activePhase);
    },
    backStep: function () {
      console.log(`step atual ${this.activePhase}`);
      this.activePhase = this.activePhase - 1;
      console.log(`step atual ${this.activePhase}`);
    },
  },
};
</script>

<style>
body {
  background-color: var(--cta-1);
}

.btn-back {
  position: relative;
  left: 50px;
  top: -10px;
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
