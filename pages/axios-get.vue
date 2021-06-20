<template>
    <div class="container">
        <h1>Axios Demo (API GET)</h1>
        <br />
        <h4>FullName : {{ fullname }}</h4>
        <h4>Gender : {{ gender }}</h4>
        <h4>Email : {{ email }}</h4>
        <img :src="picture" class="image" />

        <button type="button" @click="randomUser_GET()">Click Random</button>
    </div>
</template>

<script>
export default {
    data() {
        return {
            fullname: '',
            gender: '',
            email: '',
            picture: ''
        }
    },
    methods: {
        randomUser_GET() {
            this.$axios.$get('https://randomuser.me/api/').then(response => {
                console.log(response.results[0]) // use value response
                this.fullname = `${response.results[0].name.first} ${response.results[0].name.last}`
                this.gender = response.results[0].gender
                this.email = response.results[0].email
                this.picture = response.results[0].picture.large
            })
        }
    },
    mounted() {
        this.randomUser_GET()
    }
}
</script>

<style scoped>
.container {
    margin: 20px;
    display: flex;
    justify-content: center;
    flex-direction: column;
    align-items: center;
}
.image {
    margin: 20px;
    width: 150px;
    height: 150px;
    border-radius: 50%;
}

button {
    width: 200px;
    padding: 20px;
    background: pink;
}
</style>