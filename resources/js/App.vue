<template>
    <div class="wrapp" v-if="$auth.ready()">
        <Header></Header>
        <router-view class="main-router-view"></router-view>
        <Footer></Footer>

        <div v-if="!$auth.ready()">
            Loading...
        </div>
    </div>
</template>


<script>
    import axios from 'axios';
    import Header from './components/includes/Header'
    import Footer from './components/includes/Footer'

    export default {
        components: {
            Header,
            Footer
        },
        methods: {
            test(){
                axios.post('/auth/test')

                .then(response => {
                    console.log(response)
                })
                .catch(error => {
                    console.log(error)

                });
            }
        }
    }
</script>
<style>
    .main-router-view{
        max-width: 1280px;
        margin:40px auto;
        display: flex;
        justify-content: space-between;
    }
</style>