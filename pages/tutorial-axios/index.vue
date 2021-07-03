<template>
    <div>
        <div class="container">
            <h2>
                <u>Picture Api News</u>
            </h2>
            <img v-for="(item,index) in news" :key="index" :src="item.image" @click="openNews(item.id)" />
        </div>
    </div>
</template>

<script>
export default {
    data() {
        return {
            news: []
        }
    },
    methods: {
        getNews() {
            this.$axios.$get('http://www.server-rudydev.com/admin-project/api/news').then(response => {
                this.news = response
            })
        },
        openNews(id) {
            this.$router.push(`tutorial-axios/${id}`)
        }
    },
    mounted() {
        this.getNews()
    }
}
</script>

<style scoped>
.container {
    display: flex;
    flex-direction: column;
    align-items: center;
    margin: 20px;
    border-bottom: 1px solid;
    padding-bottom: 10px;
}
img {
    margin: 10px 0px;
    width: 500px;
    cursor: pointer;
}
</style>