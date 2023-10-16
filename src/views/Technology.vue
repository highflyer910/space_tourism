<template>
    <div class="technology">
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
                <li><router-link to="/"><span aria-hidden="true">00</span>Home</router-link></li>
                <li><router-link to="/destination"><span aria-hidden="true">01</span>Destination</router-link></li>
                <li><router-link to="/crew"><span aria-hidden="true">02</span>Crew</router-link></li>
                <li class="active"><router-link to="/technology"><span aria-hidden="true">03</span>Technology</router-link></li>
            </ul>
        </nav>  
        </header>
        <main id="main" class="grid-container grid-container--technology flow">
        <h1 class="numbered-title"><span aria-hidden="true">03</span>Space launch 101</h1>

        <div class="number-indicators flex ff-serif fs-500" role="tablist" aria-label="crew member list">
            <button @click="selectTab('launch')" :aria-selected="selectedTab === 'launch'" aria-controls="launch-tab" role="tab" data-image="launch-image"
                tabindex="0" :class="{ 'active-button': selectedTab === 'launch' }">1</button>
            <button @click="selectTab('spaceport')" :aria-selected="selectedTab === 'spaceport'" aria-controls="spaceport-tab" role="tab" data-image="spaceport-image"
                tabindex="-1" :class="{ 'active-button': selectedTab === 'spaceport' }">2</button>
            <button @click="selectTab('spacecapsule')" :aria-selected="selectedTab === 'spacecapsule'" aria-controls="spacecapsule-tab" role="tab" data-image="spacecapsule-image"
                tabindex="-1" :class="{ 'active-button': selectedTab === 'spacecapsule' }">3</button>
        </div>

        <!-- LAUNCH VEHICLE -->
        <transition name="fade" mode="out-in">
        <article v-show="selectedTab === 'launch'" class="technology-details flow" id="launch-tab" role="tabpanel" tabindex="0">
            <header class="flow flow--space-small">
                <p class="fs-700 uppercase ff-serif">Launch vehicle</p>
            </header>
            <p>A launch vehicle or carrier rocket is a rocket-propelled vehicle used to carry a
                payload from Earth's surface to space, usually to Earth orbit or beyond. Our
                WEB-X carrier rocket is the most powerful in operation. Standing 150 metres tall,
                it's quite an awe-inspiring sight on the launch pad!</p>
        </article>
        </transition>

        <!-- SPACEPORT -->
        <transition name="fade" mode="out-in">
        <article v-show="selectedTab === 'spaceport'" class="technology-details flow" id="spaceport-tab" role="tabpanel" tabindex="0">
            <header class="flow flow--space-small">
                <p class="fs-700 uppercase ff-serif">Spaceport</p>
            </header>
            <p>A spaceport or cosmodrome is a site for launching (or receiving) spacecraft,
                by analogy to the seaport for ships or airport for aircraft. Based in the
                famous Cape Canaveral, our spaceport is ideally situated to take advantage
                of the Earth’s rotation for launch.</p>
        </article>
        </transition>
        <!-- SPACE CAPSULE -->
        <transition name="fade" mode="out-in">
        <article v-show="selectedTab === 'spacecapsule'" class="technology-details flow" id="spacecapsule-tab" role="tabpanel" tabindex="0">
            <header class="flow flow--space-small">
                <p class="fs-700 uppercase ff-serif">Space capsule</p>
            </header>
            <p>A space capsule is an often-crewed spacecraft that uses a blunt-body reentry
                capsule to reenter the Earth's atmosphere without wings. Our capsule is where
                you'll spend your time during the flight. It includes a space gym, cinema,
                and plenty of other activities to keep you entertained.</p>
        </article>
        </transition>

        <picture v-show="selectedTab === 'launch'" id="launch-image">
            <source srcset="../assets/technology/image-launch-vehicle-portrait.jpg" media="(min-width: 45em)">
            <img src="../assets/technology/image-launch-vehicle-landscape.jpg" alt="Launch Vehicle image">
        </picture>
        <picture v-show="selectedTab === 'spaceport'" id="spaceport-image">
            <source srcset="../assets/technology/image-spaceport-portrait.jpg" media="(min-width: 45em)">
            <img src="../assets/technology/image-spaceport-landscape.jpg" alt="Spaceport image">
        </picture>
        <picture v-show="selectedTab === 'spacecapsule'" id="spacecapsule-image">
            <source srcset="../assets/technology/image-space-capsule-portrait.jpg" media="(min-width: 45em)">
            <img src="../assets/technology/image-space-capsule-landscape.jpg" alt="Space Capsule image">
        </picture>

    </main>
        
    </div>
</template>

<script>
import { ref } from 'vue';

export default {
    setup() {
        const selectedTab = ref('launch');
        const isMobileNavVisible = ref(false);

        const selectTab = (tabName) => {
            selectedTab.value = tabName;
        };

        const toggleMobileNav = () => {
            isMobileNavVisible.value = !isMobileNavVisible.value;
        const nav = document.querySelector('.primary-navigation');
        nav.setAttribute('data-visible', isMobileNavVisible.value.toString());
    };
    
    return {
        selectedTab,
        isMobileNavVisible,
        selectTab,
        toggleMobileNav,
    };
},
};
</script>
