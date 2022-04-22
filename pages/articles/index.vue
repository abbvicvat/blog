<template>
  	<div class="flex flex-col items-center">
        
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

        return {
            category: "all",
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

