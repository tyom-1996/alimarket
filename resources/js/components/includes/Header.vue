<template>

    <header>

        <div class="top-header-content header-item">
            <div class="header-wrapper">
                <div class="header-top-left">
                    <div class="logo">
                        <router-link to="/" >
                            <img class="logo-img" :src="logo_2">
                        </router-link>

                    </div>

                    <div class="search-bl">
                        <form action="">
                            <input placeholder="Search" type="text" class="search-input">
                            <button>
<!--                                <font-awesome-icon :icon="['fas', 'search']" />-->
                            </button>
                        </form>
                    </div>
                </div>


                <div class="header-top-right">
                    <ul class="top-menu">

                        <li class="favorites" @mouseover="favorites_hover = true" @mouseleave="favorites_hover = false">
                            <router-link to="/favorites" >
                                <span class="menu-item-icon">
                                    <font-awesome-icon  :class="{ menu_hover: favorites_hover }" :icon="['fas', 'heart']" />
                                </span>
                                <span class="menu-item-text" :class="{ menu_hover: favorites_hover }">Избранные</span>
                            </router-link>
                        </li>




                        <!--                        <li class="my-cart" @mouseover="cart_hover = true" @mouseleave="cart_hover = false">-->
<!--                            <router-link to="/cart" >-->
<!--                                <span class="menu-item-icon">-->
<!--                                    <font-awesome-icon  :class="{ menu_hover: cart_hover }" :icon="['fas', 'shopping-cart']" />-->
<!--                                </span>-->
<!--                                <span class="menu-item-text" :class="{ menu_hover: cart_hover }" >My cart</span>-->
<!--                            </router-link>-->
<!--                        </li>-->


                        <li v-if="!$auth.check()" class="sign-in" @mouseover="login_hover = true" @mouseleave="login_hover = false">
                            <router-link to="/login" >
                                <span class="menu-item-icon">
                                    <font-awesome-icon  :class="{ menu_hover: login_hover }"  :icon="['fas', 'user']" />
                                </span>
                                <span class="menu-item-text" :class="{ menu_hover: login_hover }">Войти в систему</span>
                            </router-link>
                        </li>


                        <li v-if="!$auth.check()" class="sign-up" @mouseover="register_hover = true" @mouseleave="register_hover = false">
                            <router-link to="/register" >
                                <span class="menu-item-icon">
                                    <font-awesome-icon  :class="{ menu_hover: register_hover }"  :icon="['fas', 'user-plus']" />
<!--                                    <font-awesome-icon  :class="{ menu_hover: register_hover }"  :icon="s['fa', 'UserPlus']" />-->
                                </span>
                                <span class="menu-item-text" :class="{ menu_hover: register_hover }">Регистрация</span>
                            </router-link>
                        </li>

                        <li v-if="$auth.check()" class="log-out">
                            <span>{{user_data.name}}</span>
                            <i class="fas fa-sign-out-alt"></i>
                            <a @mouseover="login_hover = true" @mouseleave="login_hover = false" href="#" @click.prevent="logout_()">Logout</a>
                        </li>

                        <li class="add-product">
                            <router-link to="/add-product" >
                                Добавить объявление
                            </router-link>

                        </li>

<!--                        <li>-->
<!--                            <div>-->
<!--                                <b-dropdown size="lg"  variant="link" toggle-class="text-decoration-none" no-caret>-->
<!--                                    <template v-slot:button-content>-->
<!--                                        &#x1f50d;<span class="sr-only">Search</span>-->
<!--                                    </template>-->
<!--                                    <b-dropdown-item href="#">Action</b-dropdown-item>-->
<!--                                    <b-dropdown-item href="#">Another action</b-dropdown-item>-->
<!--                                    <b-dropdown-item href="#">Something else here...</b-dropdown-item>-->
<!--                                </b-dropdown>-->
<!--                            </div>-->
<!--                        </li>-->

                    </ul>
                </div>
            </div>
        </div>



        <div class="bottom-header-content header-item">
            <div class="header-wrapper">

                <div class="header-bottom-left">
                    <span v-on:click="toggle_cat_modal" @mouseover="all_categories_hover = true" @mouseleave="all_categories_hover = false" :class="{ menu_hover: all_categories_hover }" >
                        Все разделы
                        <svg   height="7px" viewBox="0 0 11 7" width="11px" xmlns="http://www.w3.org/2000/svg">
                            <path :class="{ menu_hover: all_categories_hover }"  fill="#3d3f56" d="M5.4 7L0 1.6 1.4.2l4 4 4-4 1.4 1.4z"></path>
                        </svg>
                    </span>

                </div>





                <div class="header-bottom-right">
                    <ul class="all-categories-menu-list">
                        <li>
                            <router-link to="" >
                                Недвижимость
                            </router-link>
                        </li>

                        <li>
                            <router-link to="/category/auto/1" >
                                Транспорт
                            </router-link>
                        </li>

                        <li>
                            <router-link to="" >
                                Электроника
                            </router-link>
                        </li>

                        <li>
                            <router-link to="" >
                                Услуги
                            </router-link>
                        </li>

                        <li>
                            <router-link to="" >
                                Работа
                            </router-link>
                        </li>

                        <li>
                            <router-link to="" >
                                Мода и стиль
                            </router-link>
                        </li>

                        <li>
                            <router-link to="" >
                                Все для дома
                            </router-link>
                        </li>

                        <li>
                            <router-link to="" >
                                Инструменты и материалы
                            </router-link>
                        </li>

                    </ul>
                </div>

            </div>
        </div>
















        <ul v-if="open_all_cat" class="all-categories-modal">
            <li>
                <router-link to="" >
                    <img class="sidebar_icon icon-auto" :src="sidebar_icon_home">
                    Недвижимость
                </router-link>
            </li>

            <li>
                <router-link to="/category/auto/1" >
                    <img class="sidebar_icon icon-auto" :src="sidebar_icon_auto">
                    Транспорт
                </router-link>
            </li>

            <li>
                <router-link to="" >
                    <img class="sidebar_icon icon-auto" :src="sidebar_icon_electronic">
                    Электроника
                </router-link>
            </li>

            <li>
                <router-link to="" >
                    <img class="sidebar_icon icon-auto" :src="sidebar_icon_from_appliances" >
                    Бытовая техника
                </router-link>
            </li>

            <li>
                <router-link to="" >
                    <img class="sidebar_icon icon-auto" :src="sidebar_icon_from_home">
                    Все для дома
                </router-link>
            </li>

            <li>
                <router-link to="" >
                    <img class="sidebar_icon icon-auto" :src="sidebar_icon_shoes">
                    Мода и стиль
                </router-link>
            </li>

            <li>
                <router-link to="" >
                    <img class="sidebar_icon icon-auto" :src="sidebar_icon_child">
                    Детский мир
                </router-link>
            </li>

            <li>
                <router-link to="" >
                    <img class="sidebar_icon icon-auto" :src="sidebar_icon_hobbie" >
                    Культура и хобби
                </router-link>
            </li>

            <li>
                <router-link to="" >
                    <img class="sidebar_icon icon-auto" :src="sidebar_icon_animal" >
                    Животные и растения
                </router-link>
            </li>

            <li>
                <router-link to="" >
                    <img class="sidebar_icon icon-auto" :src="sidebar_icon_from_tools" >
                    Инструменты и материалы
                </router-link>
            </li>

            <li>
                <router-link to="" >
                    <img class="sidebar_icon icon-auto" :src="sidebar_icon_service" >
                    Услуги
                </router-link>
            </li>
            <li>
                <router-link to="" >
                    <img class="sidebar_icon icon-auto" :src="sidebar_icon_working" style="width: 26px;">
                    Работа
                </router-link>
            </li>





        </ul>

    </header>

</template>

<script>

    import axios from 'axios';

    export default {
        data(){
            return{
                logo_1: require('../../../images/logo.png'),
                logo_2: require('../../../images/logo2.png'),
                logo_3: require('../../../images/logo3.png'),
                logo_4: require('../../../images/logo4.png'),
                logo_5: require('../../../images/logo5.png'),
                sidebar_icon_auto: require('../../../images/sidebar_logo/auto_icon.png'),
                sidebar_icon_home: require('../../../images/sidebar_logo/home.png'),
                sidebar_icon_shoes: require('../../../images/sidebar_logo/shoes.png'),
                sidebar_icon_child: require('../../../images/sidebar_logo/child.png'),
                sidebar_icon_electronic: require('../../../images/sidebar_logo/electronic.png'),
                sidebar_icon_working: require('../../../images/sidebar_logo/working.jpg'),
                sidebar_icon_animal: require('../../../images/sidebar_logo/animal.png'),
                sidebar_icon_service: require('../../../images/sidebar_logo/service.png'),
                sidebar_icon_hobbie: require('../../../images/sidebar_logo/hobbie.jpg'),
                sidebar_icon_from_home: require('../../../images/sidebar_logo/from_home.png'),
                sidebar_icon_from_tools: require('../../../images/sidebar_logo/tools-icon.png'),
                sidebar_icon_from_appliances: require('../../../images/sidebar_logo/appliances.png'),
                favorites_hover: false,
                login_hover: false,
                cart_hover: false,
                register_hover: false,
                all_categories_hover: false,
                open_all_cat:false,
                user_data: {},
            }
        },
        methods: {
            logout_(evt) {
                axios.post('auth/logout')

                    .then(response => {
                        localStorage.removeItem('default_auth_token');
                        delete axios.defaults.headers.common['Authorization'];
                        this.$router.push('/login');
                    })
                    .catch(error => {
                        localStorage.removeItem('default_auth_token');
                        delete axios.defaults.headers.common['Authorization'];
                        // this.$router.go('/login');
                        this.$router.push('/login');
                    });
            },
            toggle_cat_modal(){
                this.open_all_cat = !this.open_all_cat;
            }
        },
        mounted() {

            // console.log(this.$store) // -> 1
            this.$root.$on('user_data',(data) => {
                this.user_data = data
            })



            if( this.$auth.check() ) {
                axios.get('auth/user')

                .then(response => {

                    if ( response.data.data === undefined ) {
                        localStorage.removeItem('default_auth_token');
                        delete axios.defaults.headers.common['Authorization'];
                        // this.$router.go('/login');
                    }else{
                        this.user_data = response.data.data;
                    }
                    console.log(this.user_data,'user')
                })
                .catch(error => {

                });
            }

            console.log('Header already.')

        }
    }
</script>

<style>
    header{
        width: 100%;
        background: white;
        box-shadow: 1px -3px 4px 1px black;
    }

    .header-item:nth-of-type(1){
        border-bottom: 1px solid #f2f2f2;
    }
    .header-item{
        min-height: 60px;
    }

    .header-wrapper{
        max-width: 1280px;
        width: 100%;
        min-height: 60px;
        display: block;
        margin: auto;
    }

    .logo-img{
        /*width: 131px;*/
        width: 174px;
    }

    .header-top-left{
        display: flex;
        align-items: center;
        min-height: 60px;
        width: 50%;
        justify-content: space-between;

    }

    .search-bl{
        width: 65%;
        padding: 0;
    }

    .search-bl form{
        position:relative;
    }

    .search-bl form button{
        background: url(https://www.list.am/img/p.png) 0 -89px;
        margin: auto;
        border: none;
        position: absolute;
        top: 0;
        bottom: 0;
        left: 4px;
        width: 22px;
        height: 22px;
        background-size: 120px 120px;
        padding: 0;
    }

    .search-bl form input {

        width: 100%;
        box-sizing: border-box;
        outline: none;
        font-size: 14px;
        border-radius: 6px;
        border: 1px solid #ccc!important;
        background-color: #fff;
        padding: 0 10px 0 28px;
        height: 36px;
    }



    .search-bl  .search-input:active,.search-bl  .search-input:focus{
        outline: none;
    }

    .search-bl button{
        border: solid 1px #ff7676;
        background: #ff7676;
        color: #fff;
        border-radius: 2rem;
        height:31px;
        width:45px;
        position: relative;
        left: -18px;


    }

    .top-header-content .header-wrapper{
        display: flex;
        justify-content: space-between;
    }


    .header-top-right{
        display: flex;
        align-items: center;
        min-height: 60px;
    }

    .top-menu{
        list-style: none;
        display:flex;
        margin-bottom: 0;
        align-items: center;
    }

    .top-menu > li {
        cursor: pointer;
        padding: 10px 15px;
        display: flex;
        align-items: center;
    }

    .menu-item-icon{
        width: 14px;
        height: 13px;
        display: inline-block;
        margin-right: 3px;
        position: relative;
        top: 0px;
    }

    .menu-item-icon svg{
        width:100%!important;
        height:100%!important;
        color: #e0e0e0;
    }

    .menu-item-text{
        color:#3d3f56;
    }

    .my-cart span svg{
        color: #3d3f56;
    }

    .top-menu > li a{
        text-decoration: none;
    }

    .menu_hover {
        color: #fc6767!important;
        fill: #fc6767!important;
        cursor:pointer;
    }

    a:focus, a:hover{
        color: unset;
    }

    .sign-up a > .menu-item-text{
        /*background: #1c1c1c;*/
        color: #3d3f56;
        /*border-radius: 19px;*/
        /*padding: 10px 10px;*/
        /*height: 28px;*/
    }

    .sign-up .menu-item-text{
        color: white;
    }

    .logo{
        width:20%;
    }

    .add-product{
        display: inline-block;
        margin: 0;
        font-weight: 400;
        font-size: 12px;
        text-decoration: none;
        color: #fff;
        cursor: pointer;
        border-radius: 4px;
        background-color: #fc6767;
        padding: 8px 16px;
        transition: background-color .2s;
    }

    .add-product a{
        color: #fff;
    }



    .bottom-header-content .header-wrapper{
        display:flex;
        justify-content:space-between;
    }

    .header-bottom-left{
        min-width: 200px;
        width: 15%;
        padding: 15px 0;
        display: flex;
        align-items: center;
    }

    .header-bottom-left > span > svg{
        display: inline-block;
        margin-left: 42px;
        vertical-align: middle;
        width: 8px;
    }
    .header-bottom-left > span {
        /*font-weight: 700;*/
        width: 100%;
        max-width: 176px;
        height: 22px;
        border-right: 1px solid silver;
        display: flex;
        align-items: center;
        color:#3d3f56;
    }

    .bottom-header-content{
        box-shadow: 0 1px 0 0 rgba(0, 0, 0, 0.06), 0 -1px 0 0 rgba(0, 0, 0, 0.06);
    }

    .all-categories-modal{
        width: 100%;
        min-height: 150px;
        background: white;
        box-shadow: 0 1px 0 0 rgba(0, 0, 0, 0.06), 0 -1px 0 0 rgba(0, 0, 0, 0.06);

        display: flex;
        list-style: none;
        /*justify-content: space-between;*/
        justify-content: flex-start;
        flex-wrap:wrap;
        max-width: 1280px;
        margin: auto;

        padding: 10px;
        box-sizing: border-box;
        align-items: center;
    }

    .all-categories-modal li {
        width:25%;
    }

    .all-categories-modal > li > a{
        color: #3d3f56;
        text-decoration:none;
    }
    .all-categories-modal > li a:hover {
        color:#fc6767;
        cursor:pointer;
    }

    .all-categories-menu-list{
        list-style: none;
        display: flex;
        align-items: center;
        padding: 15px 0;
        margin-bottom:0;

        width: 100%;
        display: flex;
        justify-content: space-between;
    }

    .all-categories-menu-list li {
        padding:0 10px;
    }

    .all-categories-menu-list > li > a{
        color: #3d3f56;
        text-decoration:none;
    }
    .all-categories-menu-list > li a:hover {
        color:#fc6767;
        cursor:pointer;
    }

    .header-bottom-right{
        display:flex;
        width:84%;

    }

</style>