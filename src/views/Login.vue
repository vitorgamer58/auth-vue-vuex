<template>
    <div class="container">
        <h1>login</h1>
        <form @submit.prevent="efetuarLogin">
            <div class="form-group">
                <label for="email">Email</label>
                <input
                    type="email"
                    class="form-control"
                    v-model="usuario.email"
                />
            </div>
            <div class="form-group">
                <label for="password">Senha</label>
                <input
                    type="password"
                    class="form-control"
                    v-model="usuario.senha"
                />
            </div>
            <button type="submit" class="btn btn-primary brn-block">
                Logar
            </button>
        </form>
        <router-link :to="{ name: 'novo.usuario' }"
            >Não possui cadastro? Cadastre-se aqui</router-link
        >
    </div>
</template>

<script>
import http from "@/http/index.js"; // Poderia ser '@/http' ou '@/http/index'

export default {
    data() {
        return {
            usuario: {},
        };
    },
    methods: {
        efetuarLogin() {
            http.post("http://localhost:8000/auth/login", this.usuario)
                .then((res) => {
                    console.log(res);
                    localStorage.setItem("token", res.data.access_token);
                    this.$router.push({ name: "gerentes" });
                })
                .catch((err) => console.log(err));
        },
    },
};
</script>

<style>
</style>