<template>
	<div class="home">
		<header class="primary-header flex">
        <div>
            <img src="../assets/shared/logo.svg" alt="space tourism logo" class="logo">
        </div>
        <button
        class="mobile-nav-toggle"
        aria-controls="primary-navigation"
        @click="toggleMobileNav"
        :aria-expanded="isMobileNavVisible ? 'true' : 'false'"
        :data-visible="isMobileNavVisible ? 'true' : 'false'">
        <span class="sr-only">Menu</span>
        </button>
        <nav>
            <ul id="primary-navigation" data-visible="false" class="primary-navigation underline-indicators flex">
                <li class="active"><router-link to="/"><span aria-hidden="true">00</span>Home</router-link></li>
                <li><router-link to="/destination"><span aria-hidden="true">01</span>Destination</router-link></li>
                <li><router-link to="/crew"><span aria-hidden="true">02</span>Crew</router-link></li>
                <li><router-link to="/technology"><span aria-hidden="true">03</span>Technology</router-link></li>
            </ul>
        </nav>  
        </header>
        
        <main id="main" class="grid-container grid-container--home">
            
            <div>
                <h1 class="text-accent fs-500 ff-sans-cond uppercase letter-spacing-1">So, you want to travel to
                <span class="d-block fs-900 ff-serif text-white">Space</span></h1>
            
                <p>Let’s face it; if you want to go to space, you might as well genuinely go to 
                outer space and not hover kind of on the edge of it. Well sit back, and relax 
                because we’ll give you a truly out of this world experience! </p>
            </div>
            <div>
                <router-link to="/destination" class="large-button uppercase ff-serif text-dark bg-white">
                    Explore
                </router-link>
            </div>
        </main>
        
    </div>
</template>

<script>
import { ref } from 'vue';

export default {
    setup() {
        const isMobileNavVisible = ref(false);
        
        const toggleMobileNav = () => {
            isMobileNavVisible.value = !isMobileNavVisible.value;
            const nav = document.querySelector('.primary-navigation');
            nav.setAttribute('data-visible', isMobileNavVisible.value.toString());
        };
        
        return {
            isMobileNavVisible,
            toggleMobileNav,
        };
    },
};
</script>