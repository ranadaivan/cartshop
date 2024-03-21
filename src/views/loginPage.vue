<template>
    <div class="login-content">
        <div class="login-itemlist">
            <h1 class="title">SHOPPING CART</h1>
            <h3 class="subtitle">Item List</h3>
            <table>
                <tr>
                    <th>Item</th>
                    <th>Price</th>
                    <th></th>
                </tr>
                <itemList itemName="Pizza" :itemPrice="35" :isDisabled="itsDisabled" />
                <itemList itemName="Burger" :itemPrice="40" :isDisabled="itsDisabled" />
                <itemList itemName="Salad" :itemPrice="50" :isDisabled="itsDisabled" />
                <itemList itemName="Ice Cream" :itemPrice="65" :isDisabled="itsDisabled" />
            </table>
        </div>
    
        <div class="login-form">
            <div class="container">
                <h3>Login</h3>
                <h5 v-if="errmsg" class="error-msg"> {{ errmsg }}</h5>
                <input type="password" v-model="password" placeholder="Enter Password">
                <button @click="login()" class="login-btn">Login</button>
            </div>
        </div>
    </div>
</template>

<script>
import itemList from '@/components/itemList.vue'

export default {
    name: 'loginPage',
    components: {
        itemList,
    },
    
    data() {
        return {
            password: '',
            errmsg: '',
            itsDisabled: true
        }
    },

    methods: {
        login() {
            if (this.password != 'ranadaivan123') {
                this.errmsg = 'Wrong password';
            } else {
                localStorage.setItem('authToken', 'true');
                this.$router.push('/shop')
            }
        }
    }
};

</script>

<style>

.login-content {
    display: grid;
    grid-template-columns: repeat(2, 1fr);
    gap: 20px;
}

.login-itemlist {
    display: flex;
    flex-direction: column;
    align-items: center;
}

.login-form {
    display: flex;
    justify-content: center;
    align-items: center;
}

.title {
    font-size: 24px;
    margin-bottom: 10px;
}

.subtitle {
    font-size: 18px;
    margin-bottom: 10px;
}

.container {
    display: flex;
    flex-direction: column;
    align-items: center;
}

.container h3 {
    margin-bottom: 10px;
    font-size: 18px;
}

.error-msg {
    color: red;
    margin-bottom: 10px;
}

input[type="password"] {
    padding: 8px;
    margin-bottom: 10px;
    border: 1px solid #ccc;
    border-radius: 5px;
    width: 200px;
}

.login-btn {
    padding: 8px 20px;
    background-color: #007bff;
    color: #fff;
    border: none;
    border-radius: 5px;
    cursor: pointer;
    transition: background-color 0.3s ease;
}

.login-btn:hover {
    background-color: #0056b3;
}

table {
    border-collapse: collapse;
    width: 100%;
    margin-bottom: 20px;
}

th, td {    
    text-align: center;
    padding: 8px;
}

th {
    background-color: #007bff;
    color: #fff;
}

td {
    border-bottom: 1px solid #ccc;
}

</style>