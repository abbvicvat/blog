<template>
  	<div class="bg-orange flex flex-col items-center">
        
        <ArticleList :articles="articles" :category="category"/>
  	</div>
</template>

<script>
import ArticleList from '../../components/ArticleList.vue'

export default {
    name: 'IndexPage',
    async asyncData({ params, redirect, $content }) {
    	let articles = await $content("articles").without('body').fetch();
        console.log(articles)
        console.log(articles.length)
        let category = params.category;

        return {
            category: category,
            articles: articles,
        }
    },

    components: {
        ArticleList
    },

    data() {
        return {
        }
    },
}
</script>

