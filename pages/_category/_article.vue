<template>
  	<div id="body">
    	<p>
			<nuxt-content :document="article"/>
			{{ category }}
    	</p>
  	</div>
</template>

<script>
export default {
  	name: 'IndexPage',
  	async asyncData({ params, redirect, $content }) {
    	let article = await $content("articles/"+params.article).fetch();
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
	#body {
		display: flex;
		justify-content: center;
	}
</style>