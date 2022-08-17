<template>
  <div id="nav">
    <router-link to="/" id="logo-url">
        <img :src="logo" :alt="alt" id="logo">
    </router-link>
    <router-link to="/">Home</router-link> |
    <router-link to="/pedidos">Pedidos</router-link>
  </div>
</template>
<script>
export default {
    name: "Navbar",
    props: ["logo", "alt"]
}
</script>
<style scoped>
    #nav {
        background-color: #ed9121;
        border-bottom: 4px solid #d19111;
        padding: 15px 50px;
        display: flex;
        justify-content: flex-end;
        align-items: center;
    }

    #nav #logo-url {
        margin: auto;
        margin-left: 0;
    }

    #logo {
        width: 40px;
        height: 40px;
    }

    #nav a {
        color: #1d170e;
        text-decoration: none;
        margin: 12px;
        transition: .5s;
        font-size: 17px;
        font-weight: 700;
    }

    #nav a:hover {
     color: #71531e ;
    }
</style>
