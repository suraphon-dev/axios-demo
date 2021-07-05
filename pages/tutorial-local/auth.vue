<template>
    <div class="container">
        <label>
            <span>Full Name:</span>
            {{ dataAuth.fullname }}
        </label>
        <label>
            <span>Name:</span>
            {{ dataAuth.name }}
        </label>
        <label>
            <span>Gender:</span>
            {{ dataAuth.gender }}
        </label>
        <label>
            <span>Email:</span>
            {{ dataAuth.email }}
        </label>

        <div>
            <button type="button" class="btn-logut" @click="logoutForm()">Logout</button>
        </div>
    </div>
</template>

<script>
export default {
    data() {
        return {
            dataAuth: ''
        }
    },
    methods: {
        logoutForm() {
            alert('logout success') // แจ้งเตือนล็อกเอ้าส์สำเร็จ
            localStorage.removeItem('auth') // คำสั่ง ลบข้อมูลใน local storage 
            this.$router.push('/tutorial-local') // คำสั่ง redirect
        }
    },
    mounted() {
        // ดึงข้อมูล auth จาก local storage มาเก็บไว้ที่ตัวแปร dataAuth
        this.dataAuth = JSON.parse(localStorage.getItem('auth'))

        // if เช็คตัวแปร dataAuth ว่ามีค่าไหม ถ้าไม่มีให้ redirect 
        if (this.dataAuth == null) {
            this.$router.push('/tutorial-local')
        }
    }
}
</script>

<style  scoped>
.container {
    margin: 20px;
    display: flex;
    flex-direction: column;
    align-items: center;
    height: 90vh;
    border: 1px solid;
    justify-content: center;
}

span {
    color: brown;
}
label {
    font-size: 18px;
    margin: 2px;
}

.btn-logut {
    width: 120px;
    height: 40px;
    border: 1px solid;
    background: #e7724f;
    border-radius: 8px;
    color: white;
    cursor: pointer;
    margin: 10px 0px;
}
</style>