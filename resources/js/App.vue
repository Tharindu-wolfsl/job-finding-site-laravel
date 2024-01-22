<template>
    <div class="app">
<!--        <Nav/>-->
        <Header/>
        <router-view></router-view>
<!--        <div class="container-xl mh-100 p-3 my-3 bg-dark text-white -xl">-->
<!--            <h1>HOME</h1>-->
<!--        </div>-->
    </div>
</template>

<script>

// import Nav from './Nav'
import Header from "./Header";

export default {
    name: "App",

    components: {
        Header,
        // Nav
    },
}
</script>

<style  scoped>

</style>
