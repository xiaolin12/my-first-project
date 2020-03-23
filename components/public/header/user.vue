<template>
    <div class="m-user">
        <template v-if="user">
            欢迎您，<span class="username">{{user}}</span>
            <el-button @click="exit">退出</el-button>
        </template>
        <template v-else>
            <nuxt-link 
            class="login"
            to="/login">登录</nuxt-link>
            <nuxt-link 
            class="register"
            to="/register">注册</nuxt-link>
        </template>
    </div>
</template>

<script>
export default {
    data(){
        return{
            user:'xiaoming'
        }
    },
    methods:{
        exit(){
            this.user=''
        }
    }
}
</script>