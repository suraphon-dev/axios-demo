<template>
    <div>
        <!-- tutorai css : contact -->
        <div class="container-title">
            <h2>My Title</h2>
            <h4>Lorem ipsum dolor sit amet consectetur adipisicing elit. Maiores, incidunt.</h4>
        </div>
        <div class="container-contact">
            <div class="card-contact" v-for="(item,index) in 3" :key="index">BOX</div>
        </div>
        <hr />

        <!-- tutorai css : box -->
        <div class="container-title">
            <h2>My Box</h2>
            <h4>Lorem ipsum dolor sit amet consectetur adipisicing elit. Maiores, incidunt.</h4>
        </div>
        <div class="container-box">
            <div class="card-box" v-for="(item,index) in 6" :key="index">BOX</div>
        </div>
        <hr />

        <!-- tutorai css : slider // import plugin bootstrap 4 -->
        <div id="carouselExampleControls" class="carousel slide" data-ride="carousel">
            <div class="carousel-inner">
                <div
                    class="carousel-item"
                    :class="{ 'active' : index == 0 }"
                    v-for="(item,index) in banner"
                    :key="index"
                >
                    <img class="d-block w-100" :src="item.image" />
                </div>
            </div>
            <a
                class="carousel-control-prev"
                href="#carouselExampleControls"
                role="button"
                data-slide="prev"
            >
                <span class="carousel-control-prev-icon" aria-hidden="true"></span>
                <span class="sr-only">Previous</span>
            </a>
            <a
                class="carousel-control-next"
                href="#carouselExampleControls"
                role="button"
                data-slide="next"
            >
                <span class="carousel-control-next-icon" aria-hidden="true"></span>
                <span class="sr-only">Next</span>
            </a>
        </div>
    </div>
</template>

<script>
export default {
    data() {
        return {
            banner: [],            
        }
    },
    methods: {
        gatBanner() {
            this.$axios.$get('http://www.server-rudydev.com/admin-project/api/banner').then(response => {
                this.banner = response
            })
        }
    },
    mounted() {
        this.gatBanner()
    }
}
</script>

<style scoped>
/* tutorai css : contact */
.container-title {
    display: flex;
    flex-direction: column;
    align-items: center;
    margin-top: 50px;
}
.container-contact {
    display: flex;
    align-items: center;
    justify-content: space-evenly;
    background-color: hsla(0, 0%, 85.9%, 0.1);
    height: 50vh;
}

.card-contact {
    display: flex;
    align-items: center;
    justify-content: center;
    border: 1px solid black;
    width: 200px;
    height: 200px;
}

/* tutorai css : box */
.container-box {
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
    margin: 20px;
}
.card-box {
    display: flex;
    align-items: center;
    justify-content: center;
    border: 1px solid black;
    background: rgb(83, 83, 250);
    color: white;
    width: 400px;
    height: 400px;
    margin: 20px;
}
</style>