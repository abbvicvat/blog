<template>
  	<div class="w-full ">
		<nuxt-content class="w-full px-4 sm:px-12 md:px-20 lg:px-24 xl:px-40" :document="article"/>
  	</div>
</template>

<script>	
export default {
  	name: 'IndexPage',
  	async asyncData({ params, redirect, $content }) {
    	let article = await $content("articles/"+params.article).fetch();
		console.log(article);
    	return {
        	category: params.category,
        	article: article,
    	}
  },

  	data() {
    	return {
    }
  }
}
</script>

<style scoped>
	
</style>