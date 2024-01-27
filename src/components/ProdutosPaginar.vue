<template>
  <p>Paginas</p>
</template>

<script>
export default {
  props: {
    produtosPorPagina: {
      type: Number,
      default: 1
    },
    produtosTotal: {
      type: Number,
      default: 1
    },
  },
}
</script>

<style></style>