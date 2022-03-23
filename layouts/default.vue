<template>
    <div>
    <header>
        <nav id="navbar" class="py-1.5 flex justify-around items-center flex-wrap">
            <nuxt-link class="mx-2" to="/"> Home </nuxt-link>
            <nuxt-link class="mx-2" to="/graph"> Graphs </nuxt-link>
            <nuxt-link class="mx-2" to="/data-structure"> Data Structures </nuxt-link>
            <nuxt-link class="mx-2" to="/dynamic-programming"> Dynamic programming </nuxt-link>

        </nav>

    </header>
    <nuxt/>
  </div>
</template>

<script>
export default {
  name: 'DefaultLayout'
}
</script>

<style scoped>
    #navbar {
        background: #d5d5d5;
    }
</style>