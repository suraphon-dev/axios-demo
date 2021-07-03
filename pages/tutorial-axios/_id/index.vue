<template>
    <div class="container">
        <h2>{{ data.title }}</h2>
        <div v-html="data.description"></div>
    </div>
</template>

<script>
export default {
    data() {
        return {
            id: this.$route.params.id,
            data: "",
        }
    },
    methods: {
        getDescriptionNews() {
            this.$axios.$get(`http://www.server-rudydev.com/admin-project/api/news/${this.id}`).then(response => {
                this.data = response
            })
        }
    },
    mounted() {
        this.getDescriptionNews()
    }
}
</script>

<style scoped>
.container {
    margin: 25px;
}
</style>