<template>
    <div class="crew">
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
                <li class="active"><router-link to="/crew"><span aria-hidden="true">02</span>Crew</router-link></li>
                <li><router-link to="/technology"><span aria-hidden="true">03</span>Technology</router-link></li>
            </ul>
        </nav>  
      </header>
      <main id="main" class="grid-container grid-container--crew flow">
      <h1 class="numbered-title"><span aria-hidden="true">02</span> Meet your crew</h1>
      
      <div class="dot-indicators flex" role="tablist" aria-label="crew member list">
        <button @click="selectTab('commander')" :aria-selected="selectedTab === 'commander'" aria-controls="commander-tab" role="tab" data-image="commander-image" tabindex="0"><span class="sr-only">The commander</span></button>
        <button @click="selectTab('mission')" :aria-selected="selectedTab === 'mission'" aria-controls="mission-tab" role="tab" data-image="mission-image" tabindex="-1"><span class="sr-only">The mission specialist</span></button>
        <button @click="selectTab('pilot')" :aria-selected="selectedTab === 'pilot'" aria-controls="pilot-tab" role="tab" data-image="pilot-image" tabindex="-1"><span class="sr-only">The pilot</span></button>
        <button @click="selectTab('crew')" :aria-selected="selectedTab === 'crew'" aria-controls="crew-tab" role="tab" data-image="crew-image" tabindex="-1"><span class="sr-only">The crew engineer</span></button>
      </div>
      
      <!-- commander -->
      <transition name="fade" mode="out-in">
      <article v-show="selectedTab === 'commander'" class="crew-details flow" id="commander-tab" role="tabpanel" tabindex="0">
        <header class="flow flow--space-small">
          <h2 class="fs-600 ff-serif uppercase">Commander</h2>
          <p class="fs-700 uppercase ff-serif">Douglas Hurley</p>
        </header>
        <p>Douglas Gerald Hurley is an American engineer, former Marine Corps pilot 
        and former NASA astronaut. He launched into space for the third time as 
        commander of Crew Dragon Demo-2.</p>
      </article> 
      </transition>
      
      <!-- mission specialist -->
      <transition name="fade" mode="out-in">
      <article v-show="selectedTab === 'mission'" class="crew-details flow" id="mission-tab" role="tabpanel" tabindex="0">
        <header class="flow flow--space-small">
          <h2 class="fs-600 ff-serif uppercase">Mission Specialist</h2>
          <p class="fs-700 uppercase ff-serif">Mark SHuttleworth</p>
        </header>
        <p>Mark Richard Shuttleworth is the founder and CEO of Canonical, the company behind
          the Linux-based Ubuntu operating system. Shuttleworth became the first South
          African to travel to space as a space tourist.</p>
      </article>
      </transition> 
      
      <!-- pilot -->
      <transition name="fade" mode="out-in">
      <article v-show="selectedTab === 'pilot'" class="crew-details flow" id="pilot-tab" role="tabpanel" tabindex="0">
        <header class="flow flow--space-small">
          <h2 class="fs-600 ff-serif uppercase">Pilot</h2>
          <p class="fs-700 uppercase ff-serif">Victor Glover</p>
        </header>
        <p>Pilot on the first operational flight of the SpaceX Crew Dragon to the
          International Space Station. Glover is a commander in the U.S. Navy where
          he pilots an F/A-18.He was a crew member of Expedition 64, and served as a
          station systems flight engineer.</p>
      </article> 
      </transition>
      
      <!-- engineer -->
      <transition name="fade" mode="out-in">
      <article v-show="selectedTab === 'crew'" class="crew-details flow" id="crew-tab" role="tabpanel" tabindex="0">
        <header class="flow flow--space-small">
          <h2 class="fs-600 ff-serif uppercase">Flight Engineer</h2>
          <p class="fs-700 uppercase ff-serif">Anousheh Ansari</p>
        </header>
        <p>Anousheh Ansari is an Iranian American engineer and co-founder of Prodea Systems.
          Ansari was the fourth self-funded space tourist, the first self-funded woman to
          fly to the ISS, and the first Iranian in space.</p>
      </article> 
      </transition>
      
      
      <picture v-show="selectedTab === 'commander'" id="commander-image">
        <source srcset="../assets/crew/image-douglas-hurley.webp" type="image/webp">
        <img src="../assets/crew/image-douglas-hurley.png" alt="Douglas Hurley">
      </picture>
      <picture v-show="selectedTab === 'mission'" id="mission-image">
        <source srcset="../assets/crew/image-mark-shuttleworth.webp" type="image/webp">
        <img src="../assets/crew/image-mark-shuttleworth.png" alt="Douglas Hurley">
      </picture>
      <picture v-show="selectedTab === 'pilot'" id="pilot-image">
        <source srcset="../assets/crew/image-victor-glover.webp" type="image/webp">
        <img src="../assets/crew/image-victor-glover.png" alt="Douglas Hurley">
      </picture>
      <picture v-show="selectedTab === 'crew'" id="crew-image">
        <source srcset="../assets/crew/image-anousheh-ansari.webp" type="image/webp">
        <img src="../assets/crew/image-anousheh-ansari.png" alt="Douglas Hurley">
      </picture>
    </main>
    </div>
</template>


<script>
import { ref } from 'vue';

export default {
  setup() {
    const selectedTab = ref('commander');
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
