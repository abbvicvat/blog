<template>
	<div class="mt-4 w-full flex flex-col items-center">
        <div class="bg-pink w-1/2 py-4 px-2 my-3 flex justify-between items-center" v-for="article in articles" :key="article.title">
            <div class="flex flex-col justify-between">
                <h1 class="mt-0"> {{ article.title_disp }} </h1>
                <p>  {{ article.category_disp }} </p>
            </div>
            <p> {{ article.date }} </p>
        </div>
	</div>
</template>

<script>

export default {
    name: 'IndexPage',

    props: {
        articles: Array,
        category: String,
    },

    created() {
        if (this.category !== "all") {
            this.articles = this.articles.filter((article) => article.category === this.category);
            console.log(123);
            console.log(this.articles);
        }
    }
}
</script>
