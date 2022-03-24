<template>    
    <div class="mt-4 w-full flex justify-center">
        <div class="w-1/2 flex flex-col">
            <h1>
                Latest Articles
            </h1>

            <nuxt-link class="bg-black text-light rounded w-full my-3 flex items-center" v-for="article in articles" :key="article.title" :to="'/'+article.category+'/'+article.title">

                <div class="w-4/5 h-full pl-3 py-6 flex flex-col justify-between">
                    <h3 class="mt-0"> {{ article.title_disp }} </h3>
                    <nuxt-link :to="'/'+article.category" style="width: fit-content;"> <p>  {{ article.category_disp }} </p> </nuxt-link>
                </div>

                <div class="bg-dark rounded w-1/5 h-full flex justify-center items-center">
                    <p> {{ article.date }} </p>
                </div>

            </nuxt-link>
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
            console.log(this.articles);
        }
    }
}
</script>
