<template>
  <div class="row">
    <div class="col-md-6">
      <div class="mt-4">
        <div class="form-group">
          <label for="especialidade">Especialidade principal</label>
          <select id="especialidade" class="form-control">
            <option selected>Selecione...</option>
            <option>...</option>
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
          <input type="checkbox" class="custom-control-input" id="dinheiro" />
          <label class="custom-control-label" for="dinheiro">Dinheiro</label>
        </div>
        <div
          class="custom-control custom-checkbox d-flex justify-content-start"
        >
          <input type="checkbox" class="custom-control-input" id="cart" />
          <label class="custom-control-label" for="cart"
            >Cartão de crédito</label
          >
        </div>
      </div>
      <a href="" class="btn btn-primary w-100 btn-rounded">PRÓXIMO</a>
    </div>
    <div class="col-md-6">
      <img src="img/desktop-pagina-2.png" alt="" class="img-responsive" />
    </div>
  </div>
</template>

<script>
export default {
  name: "PageTwo",
  props: {
    // msg: String
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
