<template>
  <div class="row">
    <div class="col-md-6">
      <div class="mt-5 alert alert-success">
        Formulário concluido com sucesso.
      </div>
    </div>
    <div class="col-md-6 d-none d-md-block">
      <img src="img/desktop-pagina-2.png" alt="" class="img-responsive" />
    </div>
  </div>
</template>

<script>
export default {
  name: "PageFour",
  props: {},
};
</script>

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
