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
        <!-- <PageOne /> -->
        <div class="row">
          <div class="col-md-6">
            <div class="mt-4">
              <div class="form-group">
                <label for="nomeCompleto">Nome Completo</label>
                <input
                  type="text"
                  class="form-control"
                  v-bind:class="{ 'is-invalid': msgError }"
                  id="nomeCompleto"
                  aria-describedby="nomeCompleto"
                  placeholder="Digite o seu nome completo"
                  v-model="nomeCompleto"
                  minLength="3"
                  maxlength="45"
                  required
                />
                <div v-if="erro" class="alert alert-danger mt-3" role="alert">
                  {{ msgError }}
                </div>
              </div>

              <div class="form-group">
                <label for="cpf">CPF</label>
                <input
                  type="text"
                  class="form-control"
                  id="cpf"
                  aria-describedby="cpf"
                  placeholder="Digite o seu CPF"
                  v-model="cpf"
                  @change="formatCPF, getUser()"
                  v-bind:class="{ 'is-invalid': msgErrorCPF }"
                  required
                />
                <div
                  v-if="existCPF"
                  class="alert alert-danger mt-3"
                  role="alert"
                >
                  {{ msgErrorCPF }}
                </div>
              </div>

              <div class="form-group">
                <label for="celular">Número do celular</label>
                <input
                  type="text"
                  class="form-control"
                  id="celular"
                  aria-describedby="celular"
                  placeholder="(00) 0 0000-0000"
                  v-model="celular"
                  @change="formatCelular"
                />
              </div>

              <div class="row">
                <div class="form-group col-md-6">
                  <label for="estado">Estado</label>
                  <select
                    id="estado"
                    class="form-control"
                    v-model="uf"
                    @change="getCity"
                  >
                    <option disabled selected>Selecione...</option>
                    <option
                      v-for="item in estado"
                      :key="item.id"
                      :value="item.id"
                    >
                      {{ item.nome }}
                    </option>
                  </select>
                </div>

                <div class="form-group col-md-6">
                  <label for="cidade">Cidade</label>
                  <select
                    id="cidade"
                    class="form-control"
                    v-model="cidadeSelecionada"
                  >
                    <option disabled selected>Selecione...</option>
                    <option
                      v-for="item in cidade"
                      :key="item.id"
                      :value="item.id"
                    >
                      {{ item.nome }}
                    </option>
                    {{
                      cidadeSelecionada
                    }}
                  </select>
                </div>
              </div>
              <!-- <a href="" class="btn btn-primary w-100 btn-rounded">PRÓXIMO</a> -->
            </div>
          </div>
          <div class="col-md-6 d-none d-md-block">
            <img src="img/desktop-pagina-1.png" alt="" class="img-responsive" />
          </div>
        </div>
        <div class="row">
          <div class="col-md-6">
            <button
              type="button"
              @click.prevent="verificarNomeCompleto()"
              class="btn btn-primary w-100 btn-rounded"
            >
              Proximo
            </button>
          </div>
        </div>
      </div>

      <div v-if="activePhase == 2">
        <!-- <PageTwo /> -->
        <div class="row">
          <div class="col-md-6">
            <div class="mt-4">
              <div class="form-group">
                <label for="especialidade">Especialidade principal</label>
                <select
                  id="especialidade"
                  class="form-control"
                  v-model="especialidade"
                >
                  <option disabled selected>Selecione...</option>
                  <option
                    v-for="item in especialidades"
                    :key="item.id"
                    :value="item.id"
                  >
                    {{ item.nome }}
                  </option>
                </select>
              </div>

              <div class="input-group mb-3">
                <div class="input-group-prepend">
                  <span class="input-group-text" id="valor">RS</span>
                </div>
                <input
                  type="text"
                  class="form-control"
                  placeholder="Valor"
                  aria-label="valor"
                  aria-describedby="valor"
                />
              </div>

              <div class="custom-control custom-checkbox">
                <input type="checkbox" class="custom-control-input" id="pix" />
                <label class="custom-control-label" for="pix">PIX</label>
              </div>
              <div class="custom-control custom-checkbox">
                <input
                  type="checkbox"
                  class="custom-control-input"
                  id="dinheiro"
                />
                <label class="custom-control-label" for="dinheiro"
                  >Dinheiro</label
                >
              </div>
              <div
                class="
                  custom-control custom-checkbox
                  d-flex
                  justify-content-start
                "
              >
                <input type="checkbox" class="custom-control-input" id="cart" />
                <label class="custom-control-label" for="cart"
                  >Cartão de crédito</label
                >
              </div>
            </div>
            <!-- <a href="" class="btn btn-primary w-100 btn-rounded">PRÓXIMO</a> -->
          </div>
          <div class="col-md-6 d-none d-md-block">
            <img src="img/desktop-pagina-2.png" alt="" class="img-responsive" />
          </div>
        </div>

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
        <PageThree
          :nomeCompleto="nomeCompleto"
          :cpf="cpf"
          :celular="celular"
          :estado="estado"
          :uf="uf"
          :cidadeSelecionada="cidadeSelecionada"
        />
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

    <p v-for="item in cidade" :key="item.id" value="item.id">
      {{ item.nome }}
    </p>
  </div>
</template>

<script>
// import PageOne from "./components/PageOne.vue";
// import PageTwo from "./components/PageTwo.vue";
import PageThree from "./components/PageThree.vue";
import PageFour from "./components/PageFour.vue";

export default {
  name: "App",
  components: {
    // PageOne,
    // PageTwo,
    PageThree,
    PageFour,
  },
  data: function () {
    return {
      activePhase: 1,
      nomeCompleto: "",
      cpf: "",
      celular: "",
      estado: "",
      uf: "",
      cidade: "",
      cidadeSelecionada: "",
      id: "",

      especialidades: "",
      especialidade: "",
      erro: false,
      msgError: "",
      msgErrorCPF: "",
      x: "",
      existCPF: false,
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

    verificarNomeCompleto: function () {
      this.erro = false;
      if (this.nomeCompleto.length <= 3) {
        this.erro = true;
        this.msgError = "No minimo 3 caracteres";
      } else if (this.nomeCompleto.length >= 45) {
        this.erro = true;
        this.msgError = "No maximo de 45 caracteres";
      }
    },
    formatCPF: function () {
      this.x = this.cpf.replace(/[^0-9]/g, "");
      this.cpf = `${this.x.substring(0, 3)}.${this.x.substring(
        3,
        6
      )}.${this.x.substring(6, 9)}-${this.x.substring(9, 11)}`;
      this.x;
    },

    formatCelular: function () {
      this.x = this.celular.replace(/[^0-9]/g, "");
      this.celular = `(${this.x.substring(0, 2)}) ${this.x.substring(
        2,
        3
      )}. ${this.x.substring(3, 7)} - ${this.x.substring(7, 11)}   `;
      this.x;
    },

    async getState() {
      const req = await fetch(
        "https://api-teste-front-end-fc.herokuapp.com/estados"
      );

      const data = await req.json();
      this.estado = data;
    },
    async getUser() {
      const req = await fetch(
        "https://api-teste-front-end-fc.herokuapp.com/profissionais"
      );

      const data = await req.json();
      this.existCPF = false;
      for (let i = 0; i < data.length; i++) {
        console.log(data[i].cpf);
        if (this.cpf == data[i].cpf) {
          // console.log("existe");
          this.existCPF = true;
          this.msgErrorCPF = "CPF já cadastrado";
        }
      }
    },

    async getCity(event) {
      const id = event.target.value;
      const req = await fetch(
        `https://api-teste-front-end-fc.herokuapp.com/cidades?estadoId=${id}`
      );

      const data = await req.json();
      this.cidade = data;
    },

    //Disparar na segunda página
    async getSpecialty() {
      const req = await fetch(
        "https://api-teste-front-end-fc.herokuapp.com/especialidades"
      );

      const data = await req.json();
      this.especialidades = data;
      // console.log(data);
    },
  },
  created() {
    this.getState();
    this.getSpecialty();
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

.custom-checkbox {
  background: var(--secondary-1);
  margin-bottom: 10px;
  padding: 15px;
  border-radius: 10px;
  display: flex;
  align-items: center;
  justify-content: start;
}

.custom-checkbox input {
  margin: 0 15px;
}
</style>
