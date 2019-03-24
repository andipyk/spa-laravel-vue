<template>
    <div>
        <div v-for="item in articles" :key="item.id">
            <h1>{{ item.title }}</h1>
            <p>{{ item.body }}</p>
        </div>
    </div>
</template>

<script>
import axios from 'axios'

export default {
    name: 'articles',
    data(){
        return {
            articles: null
        }
    },
    created() {
        this.getArticles()
    },
    methods: {
        getArticles(){
            // console.log('tes')
            axios.get('/api/articles')
                    .then( (res) => {
                        const {data:{data}} = res
                        this.articles = data
                        console.log(res)
                        
                        })
                    .catch((err) => console.error())
        }
    },
}
</script>

<style>

</style>
