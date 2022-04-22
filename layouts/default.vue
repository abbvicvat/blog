<template>
    <div>
    <header>
        <nav id="navbar" class="bg-gray pr-16 py-1.5 flex justify-end items-center flex-wrap">
            <nuxt-link class="mx-10 hoverLink" to="/"> Home </nuxt-link>
            <nuxt-link class="mx-10 hoverLink" to="/articles"> Articles </nuxt-link>
        </nav>

    </header>
    <nuxt/>
  </div>
</template>

<script>
export default {
  name: 'DefaultLayout',
};
</script>
