<template>
  <section>
    <h2>Adicionar Produtos</h2>
    <ProdutoAdicionarView/>
    <h2>Seus Produtos</h2>
    <transition-group v-if="usuario_produtos" name="list" tag="ul">
      <li v-for="(produto, index) in usuario_produtos" :key="index">
        <ProdutoItemView :produto="produto">
          <p>{{ produto.descricao }}</p>
        </ProdutoItemView>
      </li>
    </transition-group>
  </section>
</template>

<script>
import ProdutoAdicionarView from '@/components/ProdutoAdicionarView.vue';
import ProdutoItemView from "@/components/ProdutoItemView.vue";
import { mapState, mapActions } from 'vuex';

export default {
  name: "UsuarioProdutos",
  components: {
    ProdutoAdicionarView,
    ProdutoItemView
  },
  computed: {
    ...mapState(["login", "usuario", "usuario_produtos"])
  },
  methods: {
    ...mapActions(["getUsuarioProdutos"])
  },
  watch: {
    login() {
      this.getUsuarioProdutos();
    }
  },
  created() {
    if (this.login) {
      this.getUsuarioProdutos();
    }
  }
};
</script>

<style scoped>
h2 {
  margin-bottom: 20px;
}
</style>