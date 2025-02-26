<template>
  <nav class="flex flex-nowrap justify-between items-center text-gray-700 dark:text-gray-300 xl:text-xl text-base pb-8 xl:pb-12 flex-col lg:flex-row lg:space-y-0 space-y-5">
    <div>
      <h1 @click="goToRouter('Home')" style="font-family: 'Fuggles', cursive;" class="text-6xl tracking-wider font-extralight cursor-pointer">
        S NESHRAJ
      </h1>
    </div>
    <div>
      <router-link class="pr-6 font-light hover:text-gray-500" to="/">{{$t('Home')}}</router-link>
      <a class="pr-6 font-light hover:text-gray-500 cursor-pointer" @click="openResume">{{$t('Resume')}}</a>

      <i v-if="!isDarkMode" @click="ToogleDarkMode" class="fas fa-moon ml-6 cursor-pointer border px-2 py-1 rounded-xl"></i>
      <i v-else @click="ToogleDarkMode" class="fas fa-sun ml-6 cursor-pointer text-yellow-500 border px-2 py-1 rounded-xl"></i>
    </div>
  </nav>
</template>

<script>
export default {
    name: 'VNavbar',
    data() {
      return {
        IamNotInHome: true,
        isDarkMode: true,
        resumeLink: "https://drive.google.com/file/d/1rssCckqHot4NMFXlNpW4ZlKgAJtn1TWn/view?usp=sharing"
      };
    },
    watch: {
        $route(to) {
            this.IamNotInHome = to.path === "/";
        }
    },
    methods: {
      goToRouter(destination) {
        this.$router.push({ name: destination });
      },
      openResume() {
        window.open(this.resumeLink, "_blank");
      },
      ToogleDarkMode() {
        this.isDarkMode ? localStorage.theme = 'light' : localStorage.theme = 'dark';
        this.$router.go(0);
      }
    },
    created() {
      if (localStorage.theme === 'dark' || (!('theme' in localStorage) && window.matchMedia('(prefers-color-scheme: dark)').matches)) {
        document.documentElement.classList.add('dark');
        this.isDarkMode = true;
      } else {
        document.documentElement.classList.remove('dark');
        this.isDarkMode = false;
      }
    }
};
</script>

<style scoped>
  @import url("https://fonts.googleapis.com/css2?family=Fuggles&display=swap");
</style>
