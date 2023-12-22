<template>
  <div @mousemove="splashMousemove" class="splashBg min-h-screen justify-items-center place-items-center w-full grid dark:bg-black dark:text-white">
    <div class="grid w-full justify-items-center place-items-center hover:opacity-80 active:scale-90 duration-200 ease-in-out cursor-pointer">
      <img data-aos="fade-up" class="md:w-[30vw] w-[60vw]" src="/logo/seandevverse_light.svg">
      <p class="">点击以继续</p>
    </div>
  </div>
</template>

<script>
export default {
  methods: {
    splashMousemove(e) {
      const x = e.clientX / window.innerWidth * 100;
      const y = e.clientY / window.innerHeight * 100;
      this.$el.style.setProperty('--gradient-direction', `${x}% ${y}%`);
    },
  },
  mounted() {
    let darkData = localStorage.getItem('darkMode')
    if (darkData) {
      if (darkData === 'on') {
        document.body.classList.add('dark')
      } else if (darkData === 'off')
        document.body.classList.remove('dark')
    }
    else {
      if (window.matchMedia('(prefers-color-scheme: dark)').matches) {
        document.body.classList.add('dark')
      } else {
        document.body.classList.remove('dark')
      }
    }
    }
}
</script>

<style>
@font-face {
  font-family: 'Gotham';
  src: url("./assets/fonts/Gotham/GothamBook.ttf") format("truetype");
}

@font-face {
  font-family: 'MiSans';
  src: url("./assets/fonts/MiSans/MiSans-Normal.ttf") format("truetype");
}

body {
  font-family: 'MiSans', sans-serif;
}

.splashBg {
  background: radial-gradient(circle at var(--gradient-direction, center), #1e3a8a, #1f2937 70.71%);
  transition: 200ms ease-in-out;
}
</style>