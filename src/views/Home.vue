<template>
  <div>
    <section id="home" class="flex flex-col-reverse md:flex-row justify-center items-center xl:space-x-44 lg:space-x-24 sm:space-x-8 xl:p-12 mx-auto">
      <div class="flex-1 flex flex-col space-y-4">
        <div class="mt-4 xl:mt-0">
          <h2 class="2xl:text-2xl lg:text-2xl md:text-lg focus-in-expand dark:text-gray-300">
            {{$t('Hello')}}
            <span class="text-fakhti text-3xl lg:text-4xl tracking-normal font-bold focus-in-expand hover:text-turquoise">{{$t('myName')}}</span>
          </h2>
        </div>
        <div>
          <h1 class="text-turquoise text-4xl 2xl:text-6xl tracking-normal font-extrabold focus-in-expand hover:text-fakhti">{{ $t('job') }}</h1>
        </div>
        <div>
          <p class="text-sm lg:text-base leading-loose tracking-relaxed lg:leading-loose lg:tracking-relaxed text-gray-500 dark:text-gray-300 whitespace-pre-line" :class="this.$i18n.locale == 'ar' ? 'text-right' : 'text-left'">{{$t('Aboutme')}}</p>
        </div>
        
        <a href="https://drive.google.com/file/d/1aCsPOcP6OT4qVBRSkn3Oa6aOIjmNby1m/view?usp=sharing" target="_blank" class="text-xs lg:text-base bg-transparent w-full 2xl:w-1/3 hover:bg-turquoise font-semibold uppercase text-center hover:text-white dark:text-gray-400 dark:hover:text-white py-2 px-8 border border-turquoise hover:border-transparent rounded">
          {{$t('seeResume')}}
        </a>

        <v-links/>
      </div>
      <div class="flex-1">
        <img class="2xl:w-5/6 w-full slit-in-diagonal-1 rounded-lg" src="../assets/me.jpg" alt="Ahmed"/>
      </div>
    </section>

    <div class="flex justify-center items-center animate-bounce text-2xl text-gray-500 py-4">
      <div><a href="#skills"><i class="fas fa-chevron-down"></i></a></div>
    </div>

    <section id="skills">
      <skills/>
    </section>

    <section>
      <projects/>
    </section>

    <scroll-to-top ref="scrollTop" />
  </div>
</template>

<script>
import { mapGetters } from 'vuex'
import skills from "../components/Skills.vue"
import VLinks from '../components/links.vue'
import ScrollToTop from '../components/ScrollToTop.vue'
import Projects from '../components/Projects.vue'

export default {
  name: "Home",
  components: { skills, VLinks, ScrollToTop, Projects },
  data() {
    return {};
  },
  computed: {
    ...mapGetters({ isTranslated: 'isTranslated' })
  },
  methods: {
    goToResume() {
      this.$router.push({ name: 'Resume' })
    }
  },
  mounted() {
    window.addEventListener('scroll', this.$refs.scrollTop.scrollListener)
  },
  destroyed() {
    this.$store.commit('ToggleIsTranslated')
  }
};
</script>

<style scoped>
.typicalWrapper::after {
  content: "|";
  animation: blink 1s infinite step-start;
}
@keyframes blink {
  50% {
    opacity: 0;
  }
}

@keyframes slit-in-diagonal-1 {
  0% {
    transform: translateZ(-800px) rotate3d(1, 1, 0, 90deg);
    animation-timing-function: ease-in;
    opacity: 0;
  }
  54% {
    transform: translateZ(-160px) rotate3d(1, 1, 0, 87deg);
    animation-timing-function: ease-in-out;
    opacity: 1;
  }
  100% {
    transform: translateZ(0) rotate3d(1, 1, 0, 0);
    animation-timing-function: ease-out;
  }
}

@keyframes focus-in-expand {
  0% {
    letter-spacing: -0.5em;
    filter: blur(12px);
    opacity: 0;
  }
  100% {
    filter: blur(0);
    opacity: 1;
  }
}

.slit-in-diagonal-1 {
  -webkit-animation: slit-in-diagonal-1 0.45s ease-out both;
  animation: slit-in-diagonal-1 0.45s ease-out both;
}

.focus-in-expand {
  animation: focus-in-expand 0.8s cubic-bezier(0.25, 0.46, 0.45, 0.94) both;
}
</style>
