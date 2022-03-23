<template>
	<div>
		<Description/>
        <ArticleList class="mt-10" :articles="articles" :category="category"/>
	</div>
</template>

<script>
import Description from '../components/Description.vue'
export default {
    name: 'IndexPage',

    async asyncData({ params, redirect, $content }) {
    	let articles = await $content("articles").without('body').fetch();
        console.log(articles)
        console.log(articles.length)
        let category = "all";

        return {
            category: category,
            articles: articles,
        }
    },

    components: {
        Description
    },
}
</script>
