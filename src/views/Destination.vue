<template>
    <div class="destination">
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
                <li class="active"><router-link to="/destination"><span aria-hidden="true">01</span>Destination</router-link></li>
                <li><router-link to="/crew"><span aria-hidden="true">02</span>Crew</router-link></li>
                <li><router-link to="/technology"><span aria-hidden="true">03</span>Technology</router-link></li>
            </ul>
        </nav>  
        </header>
        <main id="main" class="grid-container grid-container--destination flow">
    <h1 class="numbered-title"><span aria-hidden="true">01</span> Pick your destination</h1>
    
    <transition name="fade" mode="out-in">
    <picture v-show="selectedTab === 'moon'" id="moon-image">
      <source srcset="../assets/destination/image-moon.webp" type="image/webp">
      <img src="../assets/destination/image-moon.png" alt="the moon">
    </picture>
    </transition>
    <transition name="fade" mode="out-in">
    <picture v-show="selectedTab === 'mars'" id="mars-image">
      <source srcset="../assets/destination/image-mars.webp" type="image/webp">
      <img src="../assets/destination/image-mars.png" alt="the planet mars">
    </picture>
    </transition>
    <transition name="fade" mode="out-in">
    <picture v-show="selectedTab === 'europa'" id="europa-image">
      <source srcset="../assets/destination/image-europa.webp" type="image/webp">
      <img src="../assets/destination/image-europa.png" alt="the planet europa">
    </picture>
    </transition>
    <transition name="fade" mode="out-in">
    <picture v-show="selectedTab === 'titan'" id="titan-image">
      <source srcset="../assets/destination/image-titan.webp" type="image/webp">
      <img src="../assets/destination/image-titan.png" alt="the moon titan">
    </picture>
    </transition>
    
    
    <div class="tab-list underline-indicators flex" role="tablist" aria-label="destination list">
        <button @click="selectTab('moon')" :aria-selected="selectedTab === 'moon'" role="tab" aria-controls="moon-tab" class="uppercase ff-sans-cond text-accent letter-spacing-2" tabindex="0" data-image="moon-image">Moon</button>
        <button @click="selectTab('mars')" :aria-selected="selectedTab === 'mars'" role="tab" aria-controls="mars-tab" class="uppercase ff-sans-cond text-accent letter-spacing-2" tabindex="-1" data-image="mars-image">Mars</button>
        <button @click="selectTab('europa')" :aria-selected="selectedTab === 'europa'" role="tab" aria-controls="europa-tab" class="uppercase ff-sans-cond text-accent letter-spacing-2" tabindex="-1" data-image="europa-image">Europa</button>
        <button @click="selectTab('titan')" :aria-selected="selectedTab === 'titan'" role="tab" aria-controls="titan-tab" class="uppercase ff-sans-cond text-accent letter-spacing-2" tabindex="-1" data-image="titan-image">Titan</button>
    </div>

    <!-- The moon -->
    <transition name="fade" mode="out-in">
    <article v-show="selectedTab === 'moon'" class="destination-info flow" id="moon-tab" tabindex="0" role="tabpanel">
      <h2 class="fs-800 uppercase ff-serif">Moon</h2>

      <p>See our planet as you’ve never seen it before. A perfect relaxing trip away to help 
      regain perspective and come back refreshed. While you’re there, take in some history 
      by visiting the Luna 2 and Apollo 11 landing sites.</p>
      
      <div class="destination-meta flex">
        <div>
          <h3 class="text-accent fs-200 uppercase">Avg. distance</h3>
          <p class="ff-serif uppercase">384,400 km</p>
        </div>
        <div>
          <h3 class="text-accent fs-200 uppercase">Est. travel time</h3>
          <p class="ff-serif uppercase">3 days</p>
        </div>
      </div>
    </article>
    </transition>
    
    
    <!-- Mars -->
    <transition name="fade" mode="out-in">
    <article v-show="selectedTab === 'mars'" class="destination-info flow" id="mars-tab" tabindex="0"  role="tabpanel">
      <h2 class="fs-800 uppercase ff-serif">Mars</h2>

      <p>Don’t forget to pack your hiking boots. You’ll need them to tackle Olympus Mons, 
  the tallest planetary mountain in our solar system. It’s two and a half times 
  the size of Everest!</p>
      
      <div class="destination-meta flex">
        <div>
          <h3 class="text-accent fs-200 uppercase">Avg. distance</h3>
          <p class="ff-serif uppercase">225 mil. km</p>
        </div>
        <div>
          <h3 class="text-accent fs-200 uppercase">Est. travel time</h3>
          <p class="ff-serif uppercase">9 months</p>
        </div>
      </div>
    </article>
    </transition>
    
    <!-- Europa -->
    <transition name="fade" mode="out-in">
    <article v-show="selectedTab === 'europa'" class="destination-info flow" id="europa-tab" tabindex="0"  role="tabpanel">
      <h2 class="fs-800 uppercase ff-serif">Europa</h2>

      <p>The smallest of the four Galilean moons orbiting Jupiter, Europa is a 
  winter lover’s dream. With an icy surface, it’s perfect for a bit of 
  ice skating, curling, hockey, or simple relaxation in your snug 
  wintery cabin.</p>
      <div class="destination-meta flex">
        <div>
          <h3 class="text-accent fs-200 uppercase">Avg. distance</h3>
          <p class="ff-serif uppercase">628 mil. km</p>
        </div>
        <div>
          <h3 class="text-accent fs-200 uppercase">Est. travel time</h3>
          <p class="ff-serif uppercase">3 years</p>
        </div>
      </div>
    </article>
    </transition>
    
    <!-- Titan -->
    <transition name="fade" mode="out-in">
    <article v-show="selectedTab === 'titan'" class="destination-info flow" id="titan-tab" tabindex="0"  role="tabpanel">
      <h2 class="fs-800 uppercase ff-serif">Titan</h2>

      <p>The only moon known to have a dense atmosphere other than Earth, Titan 
  is a home away from home (just a few hundred degrees colder!). As a 
  bonus, you get striking views of the Rings of Saturn.</p>
      
      <div class="destination-meta flex">
        <div>
          <h3 class="text-accent fs-200 uppercase">Avg. distance</h3>
          <p class="ff-serif uppercase">1.6 bil. km</p>
        </div>
        <div>
          <h3 class="text-accent fs-200 uppercase">Est. travel time</h3>
          <p class="ff-serif uppercase">7 years</p>
        </div>
      </div>
    </article>
  </transition>
  </main>
        
    </div>
</template>

<script>
import { ref } from 'vue';

export default {
  setup() {
    const selectedTab = ref('moon');
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