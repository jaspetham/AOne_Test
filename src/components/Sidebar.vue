<script setup>
    function menuOpen(){
        var navIcon = document.getElementById("nav-icon1");
        var mainDom = document.getElementById("main");
        mainDom.classList.toggle("menuOpen");
        navIcon.classList.toggle("open");
    }
</script>

<template>
    <section id="sidebar" class="bg-sidebar">
        <div class="hamburger flex">
            <button @click="menuOpen()" class="mobileOnly" id="nav-icon1">
                <span></span>
                <span></span>
                <span></span>
            </button>
        </div>
        <router-link to="/" class="logo-wrap flex items-center">
            <img src="/assets/aone-logo.png" alt="logo" class="logo">
            <span class="fs-600 font-bold text-white logo-text">AOne</span>
        </router-link>
        <ul class="side-menus flow">
            <li>
                <router-link to="/about" id="aboutLink" class="text-light-grey flex items-center menu">
                    <div class="menu-icon">
                        <svg width="18" height="18" viewBox="0 0 18 18" fill="none" xmlns="http://www.w3.org/2000/svg">
                            <path d="M9 16.5C13.1421 16.5 16.5 13.1421 16.5 9C16.5 4.85786 13.1421 1.5 9 1.5C4.85786 1.5 1.5 4.85786 1.5 9C1.5 13.1421 4.85786 16.5 9 16.5Z" stroke="#BDBDBD" stroke-linecap="round" stroke-linejoin="round"/>
                            <path d="M9 12V9" stroke="#BDBDBD" stroke-linecap="round" stroke-linejoin="round"/>
                            <path d="M9 6H9.0075" stroke="#BDBDBD" stroke-linecap="round" stroke-linejoin="round"/>
                        </svg>
                    </div>
                    <span class="fs-400 menu-text">About</span>
                </router-link>
            </li>
            <li>
                <router-link :to="{name : 'users', params: { id: '1'}}" id="usersLink" class="text-light-grey flex items-center menu">
                    <div class="menu-icon">
                        <svg width="18" height="19" viewBox="0 0 18 19" fill="none" xmlns="http://www.w3.org/2000/svg">
                            <path d="M12.75 15.8492V14.3492C12.75 13.5536 12.4339 12.7905 11.8713 12.2279C11.3087 11.6653 10.5456 11.3492 9.75 11.3492H3.75C2.95435 11.3492 2.19129 11.6653 1.62868 12.2279C1.06607 12.7905 0.75 13.5536 0.75 14.3492V15.8492" stroke="#BDBDBD" stroke-linecap="round" stroke-linejoin="round"/>
                            <path d="M6.75 8.34924C8.40685 8.34924 9.75 7.0061 9.75 5.34924C9.75 3.69239 8.40685 2.34924 6.75 2.34924C5.09315 2.34924 3.75 3.69239 3.75 5.34924C3.75 7.0061 5.09315 8.34924 6.75 8.34924Z" stroke="#BDBDBD" stroke-linecap="round" stroke-linejoin="round"/>
                            <path d="M17.25 15.8492V14.3492C17.2495 13.6845 17.0283 13.0388 16.621 12.5135C16.2138 11.9881 15.6436 11.6129 15 11.4467" stroke="#BDBDBD" stroke-linecap="round" stroke-linejoin="round"/>
                            <path d="M12 2.44672C12.6453 2.61194 13.2173 2.98724 13.6257 3.51345C14.0342 4.03966 14.2559 4.68684 14.2559 5.35297C14.2559 6.01909 14.0342 6.66628 13.6257 7.19248C13.2173 7.71869 12.6453 8.09399 12 8.25922" stroke="#BDBDBD" stroke-linecap="round" stroke-linejoin="round"/>
                        </svg>
                    </div>
                    <span class="fs-400 menu-text">Users</span>
                </router-link>
            </li>
        </ul>
    </section>
</template>

<style>
    /* Icon 1 */
    #nav-icon1 {
        width:100%;
        max-width: 30px;
        height:20px;
        position: relative;
        -webkit-transform: rotate(0deg);
        -moz-transform: rotate(0deg);
        -o-transform: rotate(0deg);
        transform: rotate(0deg);
        -webkit-transition: .5s ease-in-out;
        -moz-transition: .5s ease-in-out;
        -o-transition: .5s ease-in-out;
        transition: .5s ease-in-out;
        cursor: pointer;
        margin-bottom:0.5rem;
    }

    #nav-icon1 span{
        display: block;
        position: absolute;
        height: 3px;
        width: 100%;
        background: var(--clr-blue);
        border-radius: 9px;
        opacity: 1;
        left: 0;
        -webkit-transform: rotate(0deg);
        -moz-transform: rotate(0deg);
        -o-transform: rotate(0deg);
        transform: rotate(0deg);
        -webkit-transition: .25s ease-in-out;
        -moz-transition: .25s ease-in-out;
        -o-transition: .25s ease-in-out;
        transition: .25s ease-in-out;
    }

    #nav-icon1 span:nth-child(1) {
        top: 0px;
    }

    #nav-icon1 span:nth-child(2) {
        top: 9px;
    }

    #nav-icon1 span:nth-child(3) {
        top: 18px;
    }

    #nav-icon1.open span:nth-child(1) {
        top: 9px;
        -webkit-transform: rotate(135deg);
        -moz-transform: rotate(135deg);
        -o-transform: rotate(135deg);
        transform: rotate(135deg);
    }

    #nav-icon1.open span:nth-child(2) {
        opacity: 0;
        left: -60px;
    }

    #nav-icon1.open span:nth-child(3) {
        top: 9px;
        -webkit-transform: rotate(-135deg);
        -moz-transform: rotate(-135deg);
        -o-transform: rotate(-135deg);
        transform: rotate(-135deg);
    }

    #sidebar{
        width:15%;
        transition: width .5s ease-out;
    }
    #main.menuOpen #sidebar{
        width:35%;
    }
    .hamburger{
        padding:1rem 0.5rem;
        margin-left: 12%;
    }
    .logo-wrap,.menu{
        justify-content: center;
    }
    .menu,.logo-wrap{
        padding:0;
    }
    .menu-text,.logo-text{
        width:0;
        opacity: 0;
        visibility: hidden;
        transition: opacity .5s ease-out, width .1s ease;
    }
    #main.menuOpen :is(.menu-text,.logo-text){
        width:auto;
        opacity: 1;
        visibility: visible;
        margin-left: 0.5rem;
    }

    #sidebar img{
        height: 40px;
    }
    .side-menus{
        margin-top:0.5rem;
    }
    .menu:hover,.menu.router-link-active{
        background:var(--clr-brown);
    }
    /* tablet size */
    @media (min-width: 35em) {
        #sidebar{
            width:25%;
        }
        #sidebar img{
            height: auto;
        }
        .logo-wrap,.menu{
            justify-content: initial;
            column-gap: 1rem;
        }
        .menu-text{
            width:auto;
            opacity: 1;
            visibility: visible;
        }
        
        .menu-text,.logo-text{
            width:auto;
            opacity: 1;
            visibility: visible;
        }

        .menu,.logo-wrap{
            padding:1rem 2rem;
        }
    }

    /* laptop size */
    @media (min-width: 45em) {}
</style>
