<template>
  	<div class="w-full px-32">
		<nuxt-content class="bg-pink w-full" :document="article"/>
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