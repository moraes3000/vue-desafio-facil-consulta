<template>
  <div class="row">
    <div class="col-md-6">
      <div>
        <p>
          <strong>Nome completo </strong><br />
          {{ nomeCompleto }}
        </p>
      </div>
      <div>
        <p>
          <strong>CPF </strong><br />
          {{ cpf }}
        </p>
      </div>
      <div>
        <p>
          <strong>Número de celular ou </strong><br />
          {{ celular }}
        </p>
      </div>
      <div>
        <p>
          <strong>Estado/Cidade </strong><br />
          <!-- {{ estado }} ---  -->
          {{ uf }} - {{ cidadeSelecionada }}
        </p>
      </div>
      <div>
        <p><strong>Preço da consulta </strong><br />Preço da consulta</p>
      </div>
      <div>
        <p><strong>Forma de pagamento </strong><br />Forma de pagamento</p>
      </div>

      <!-- <a href="" class="btn btn-primary w-100 btn-rounded"
        >CADASTRAR PROFISSIONAL</a
      >
      <a href="" class="btn w-100 btn-rounded">Editar Cadastro</a> -->
    </div>
    <div class="col-md-6 d-none d-md-block">
      <img src="img/desktop-pagina-2.png" alt="" class="img-responsive" />
    </div>
  </div>
</template>

<script>
export default {
  name: "PageThree",
  props: {
    // msg: String
    nomeCompleto: String,
    cpf: String,
    celular: String,
    estado: Array,
    uf: String,
    cidadeSelecionada: String,
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
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
