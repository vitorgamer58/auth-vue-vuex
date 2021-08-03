<template>
    <nav class="navbar navbar-expand-lg navbar-bytebank">
        <a class="navbar-brand" href="#">ByteBank</a>
        <button
            class="navbar-toggler"
            type="button"
            data-toggle="collapse"
            data-target="#navbarSupportedContent"
            aria-controls="navbarSupportedContent"
            aria-expanded="false"
            aria-label="Toggle navigation"
        >
            <span class="navbar-toggler-icon"></span>
        </button>
        <div class="collapse navbar-collapse" id="navbarSupportedContent">
            <BarraNavegacaoLogado v-if="usuarioEstaLogado" />
            <BarraNavegacaoDeslogado v-else />
        </div>
    </nav>
</template>

<script>
import BarraNavegacaoLogado from './BarraNavegacaoLogado.vue'
import BarraNavegacaoDeslogado from './BarraNavegacaoDeslogado.vue'
export default {
    components: {
        BarraNavegacaoLogado,
        BarraNavegacaoDeslogado
    },
    methods: {
        efetuarLogout() {
            localStorage.removeItem("token");
            this.$router.push({ name: "login" });
        },
    },
    computed: {
        usuarioEstaLogado() {
            return Boolean(localStorage.getItem("token"));
        },
    }
};
</script>

<style>
</style>