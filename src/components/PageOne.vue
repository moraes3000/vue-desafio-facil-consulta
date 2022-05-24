<template>
  <div class="row">
    <div class="col-md-6">
      <form class="mt-4">
        <div class="form-group">
          <label for="nomeCompleto">Nome Completo</label>
          <input
            type="text"
            class="form-control"
            id="nomeCompleto"
            aria-describedby="nomeCompleto"
            placeholder="Digite o seu nome completo"
          />
        </div>

        <div class="form-group">
          <label for="cpf">CPF</label>
          <input
            type="text"
            class="form-control"
            id="cpf"
            aria-describedby="cpf"
            placeholder="Digite o seu CPF"
          />
        </div>

        <div class="form-group">
          <label for="celular">Número do celular</label>
          <input
            type="text"
            class="form-control"
            id="celular"
            aria-describedby="celular"
            placeholder="(00) 0 0000-0000"
          />
        </div>

        <div class="row">
          <div class="form-group col-md-6">
            <label for="estado">Estado</label>
            <select id="estado" class="form-control">
              <option selected>Selecione...</option>
              <option>...</option>
            </select>
          </div>

          <div class="form-group col-md-6">
            <label for="cidade">Cidade</label>
            <select id="cidade" class="form-control">
              <option selected>Selecione...</option>
              <option>...</option>
            </select>
          </div>
        </div>
        <a href="" class="btn btn-primary w-100 btn-rounded">PRÓXIMO</a>
      </form>
    </div>
    <div class="col-md-6">
      <img src="img/desktop-pagina-1.png" alt="" class="img-responsive" />
    </div>
  </div>
</template>

<script>
export default {
  name: "PageOne",
  props: {
    // msg: String
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
