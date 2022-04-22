<template>    
    <div class="mt-4 w-full flex justify-center">
        <div class="w-1/2 flex flex-col">
            <div class="pt-2 flex justify-between items-center">
                <h1>
                    Latest Articles
                </h1>
            </div>
            <hr>

            <div class="flex flex-row justify-between flex-wrap">
                <nuxt-link class="rounded mx-4 hoverLink" to="/articles/">
                    <h3>All</h3>
                </nuxt-link>

                <nuxt-link class="rounded mx-4 hoverLink" to="/articles/graph">
                    <h3>Graph</h3>
                </nuxt-link>

                <nuxt-link class="rounded mx-4 hoverLink" to="/articles/data-structure">
                    <h3>Data Structure</h3>
                </nuxt-link>

                <nuxt-link class="rounded mx-4 hoverLink" to="/articles/dynamic-programming">
                    <h3>Dynamic Programming</h3>
                </nuxt-link>
            </div>

            <nuxt-link class="hoverLink2 bg-black text-light rounded w-full my-3 flex flex-col md:flex-row items-center" v-for="article in articles" :key="article.title" :to="'/articles/'+article.categories[0]+'/'+article.title">
                <div class="w-full md:w-4/5 h-full px-3 py-6 flex flex-col justify-between">
                    <h3 class="mt-0"> {{ article.title_disp }} </h3>
                    <div class="flex flex-row">
                        <nuxt-link class="mr-5 hoverLink" v-for="category in article.categories" :key="category" :to="'/articles/'+category" style="height: fit-content; width: fit-content;"> <p>  {{ all_categories[category].display }} </p> </nuxt-link>
                    </div>
                </div>

                <div class="bg-dark rounded w-full md:w-1/5 h-1/3 md:h-full pl-3 md:pl-0 flex flex-row items-start md:justify-center md:items-center">
                    <p class=""> {{ article.date }} </p>
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
        this.category = this.category.toLowerCase();
        if (this.category !== "all") {
            for (let name in this.all_categories) {
                let current_category = this.all_categories[name];
                if (current_category.alias.includes(this.category)) this.category = current_category.alias[0];
            }

            this.articles = this.articles.filter((article) => article.categories.includes(this.category));
            console.log(this.articles);
        }
        this.articles.sort((a, b) => (a.createdAt < b.createdAt) ? 1 : -1);
    },

    data() {
        return {
            all_categories: {
                "graph": {
                    display: "Graph",
                    alias: ["graph", "graphs"]
                },
                "dynamic-programming": {
                    display: "Dynamic Programming",
                    alias: ["dynamic-programming", "dynamic programming", "dp"]
                },
                "data-structure": {
                    display: "Data Structure",
                    alias: ["data-structure", "data structure", "data structures", "data-structures", "ds"]
                }
            }
        }
    }
}
</script>
