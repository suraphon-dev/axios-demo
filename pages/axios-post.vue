<template>
    <div class="container">
        <h1>Axios Demo (API POST)</h1>
        <br />
        <div v-show="fullname != ''" class="container">
            <h4>FullName : {{ fullname }}</h4>
            <h4>Gender : {{ gender }}</h4>
            <h4>Email : {{ email }}</h4>
            <img :src="picture" class="image" />
        </div>

        <div>
            <button type="button" @click="randomUser_POST()">Click Post API</button>
            <button
                v-show="fullname != ''"
                type="button"
                class="bt-reset"
                @click="resetData()"
            >Reset Data</button>
        </div>
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
        randomUser_POST() {
            const formData = {
                userId: 1,
                fullame: 'Joao Faure',
                email: 'joao.faure@example.com',
                gender: 'male',
                picture: 'https://randomuser.me/api/portraits/men/86.jpg'
            }
            this.$axios.$post('https://jsonplaceholder.typicode.com/posts', formData).then(response => {
                console.log(response) // use value response
                this.fullname = response.fullame
                this.gender = response.gender
                this.email = response.email
                this.picture = response.picture
            })
        },

        resetData() {
            this.fullname = ''
            this.gender = ''
            this.email = ''
            this.picture = ''
        }
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
    color: white;
    background: blue;
}
.bt-reset {
    width: 200px;
    padding: 20px;
    color: white;
    background: green;
}
</style>