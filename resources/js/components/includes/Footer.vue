<template>
    <footer>
        <div class="footer-top">
            <ul>
                <li><router-link to="/catalog" > Catalog </router-link></li>
                <li><router-link to="/privacy" > Privacy Policy </router-link></li>
                <li><router-link to="/terms" > Terms of Use </router-link></li>
                <li><router-link to="/cpr-protection" > Copyright Protection </router-link></li>
                <li><router-link to="/support" > Support </router-link></li>
                <li><router-link to="/about" >About AliMarket</router-link></li>
                <li><router-link to="/seller" > Become a seller </router-link></li>
            </ul>
        </div>


        <div class="footer-bottom">
            <p>© 2019 SIA AliMarket (Armenia)</p>
        </div>
    </footer>
</template>

<script>
    export default {
        mounted() {
            console.log('Footer already.')
        }
    }
</script>


<style>

    footer{
        background: white;
    }
    .footer-top{
        max-width: 1280px;
        min-height: 52px;
        margin: auto;
        border-bottom: 1px solid #f2f2f2;

        display: flex;
        align-items: center;
        justify-content: flex-start;
    }


    .footer-bottom{
        max-width: 1280px;
        min-height: 52px;
        margin: auto;
    }

    .footer-top ul{
        display: flex;
        margin-bottom: 0;
    }

    .footer-top ul li{
        list-style: none;
        padding-right: 16px;
    }

    .footer-top ul li a{
        color:#9697a1;
    }

    .footer-bottom{
        display: flex;
        align-items: center;
    }

    .footer-bottom p{
        margin-bottom: 0!important;
        color:#9697a1;
    }

</style>