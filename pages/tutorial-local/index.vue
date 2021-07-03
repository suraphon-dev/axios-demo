<template>
    <div class="container">
        <div class="label">
            <label>username:</label>
            <input v-model="username" type="text" placeholder="username" />
        </div>
        <div class="label">
            <label>password:</label>
            <input v-model="password" type="password" placeholder="password" />
        </div>
        <div class="footer">
            <button type="button" class="btn-cancel" @click="resetForm()">Cancel</button>
            <button type="button" class="btn-login" @click="submitForm()">Login</button>
        </div>
    </div>
</template>

<script>
export default {
    data() {
        return {
            username: '',
            password: '',

            // mockup username
            userInfo: {
                username: 'admin',
                password: '123456',
                name: 'Developer',
                fullname: 'Frontend Developer',
                gender: 'male',
                email: 'developer@gmail.com'
            }
        }
    },
    methods: {
        resetForm() {
            this.username = ''
            this.password = ''
        },
        submitForm() {
            // if username, password ตรงกับข้อมูลที่่เรา mockup userInfo
            if (this.username == this.userInfo.username && this.password == this.userInfo.password) {
                alert('login success') // แจ้งเตือนล็อกอินสำเร็จ
                localStorage.setItem('auth', JSON.stringify(this.userInfo)) // นำข้อมูลเก็บไว้ที่ local storage
                this.$router.push('/tutorial-local/auth') // redirect ไปยังหน้าที่ต้องการ
            } else {
                // else ถ้าเงื่อนไขไม่ตรง 
                alert('error login') // แจ้งเตือนล็อกอินไม่สำเร็จ
                this.resetForm() // call function เคียค่า username, password
            }
        }
    }
}
</script>

<style scoped>
.container {
    margin: 20px;
    display: flex;
    flex-direction: column;
    align-items: center;
    height: 90vh;
    border: 1px solid;
    justify-content: center;
}
.label {
    width: 100%;
    text-align: center;
}

label {
    margin: 0px 10px;
}
input {
    width: 35%;
    padding: 12px 20px;
    margin: 8px 0;
    box-sizing: border-box;
}
.footer {
    margin: 10px;
}

.btn-cancel {
    width: 120px;
    height: 40px;
    border: 1px solid;
    background: #e7724f;
    border-radius: 8px;
    color: white;
    cursor: pointer;
}
.btn-login {
    width: 120px;
    height: 40px;
    border: 1px solid;
    background: #4f67e7;
    border-radius: 8px;
    color: white;
    cursor: pointer;
}
.btn-login:hover,
.btn-cancel:hover {
    border: 1px solid black;
}
</style>