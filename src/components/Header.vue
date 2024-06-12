<script setup>

import { ref, onMounted } from 'vue';


const isOpen = ref(false);

const manubar = ref(0);
const toggleNav = ref(false);

const lastScrollTop = ref(0);
const scrolledDown = ref(false);

const header = ( () =>{
  window.addEventListener("scroll", handleScroll);
})

const sidemenu = ( () =>{
  window.addEventListener("click", handleMenu);
})
onMounted(() => {
  header()
  sidemenu()
});

const handleMenu = () => {
  const manuBar = window.pageYOffset || document.documentElement.manuBar;
  toggleNav.value = manuBar >manubar.value;
  toggleNav.value = manuBar;
};

const handleScroll = () => {
  const scrollTop = window.pageYOffset || document.documentElement.scrollTop;
  scrolledDown.value = scrollTop > lastScrollTop.value;
  lastScrollTop.value = scrollTop;
};

</script>

<template>
    <div id="navbar" :class="{ '-top-40': scrolledDown, 'top-0': !scrolledDown }"  class=" opacity-100  z-50 bg-primary fixed flex justify-between w-full top-0 h-[100px] pt-2 px-7.5p items-center transition-all ease-in-out duration-500" >

        <RouterLink to="/">
            <img src="@/assets/images/logo/logo.png" class="w-full h-16">
        </RouterLink>
        <div class="flex items-center gap-5">
            <div class="flex items-center gap-2">
                <h1 class="font-semibold text-xl text-Color uppercase">light</h1>
                <label class="switch relative inline-block w-11  h-5 ">
                    <input class="opacity-0 w-0 h-0" type="checkbox">
                    <span class="slider round  absolute cursor-pointer top-0 left-0 right-0 bottom-0 bg-headertogol transition duration-400"></span>
                </label>
            </div>
            <div  class="elegance-hamburger-menu flex justify-center items-center gap-2  cursor-pointer " @click="toggleNav = !toggleNav">
                <h2 @click="isOpen = true" class="font-semibold text-xl text-Color uppercase hover:text-secondary">Menu</h2>
                <div @click="isOpen = true" class="elegance-hamburger-menu__btn"  :class="{'elegance-hamburger-menu__btn--active' : toggleNav}">
                    <span></span>
                </div>
            </div>
        </div>
    </div>
  
      <aside  :class="{ 'right-0': isOpen , ' -right-[600px]': !isOpen }" class="opacity-100  z-50 transition-all ease-in-out duration-1000 fixed  bg-manubar opacity-96 w-full h-screen max-w-lg top-0  bottom-0  overflow-auto " >
        <div class="text-white ms-5 mt-2">
            <div class="mt-10 ps-10">
              <div :class="{ 'ms-80': isOpen, 'ms-0': !isOpen }"  class="flex  pe-10  transition-all ease-in-out duration-[1000ms]">
                  <div  class="elegance-hamburger-menu  items-center gap-2  cursor-pointer " @click="toggleNav = !toggleNav">
                      <h2 @click="isOpen = false" class="font-light text-lg text-white uppercase">close</h2>
                      <div @click="isOpen = false" class="elegance-hamburger-menu__btn text-white"  :class="{'elegance-hamburger-menu__btn--active' : toggleNav}">
                          <span></span>
                      </div>
                  </div>
              </div>
              
                <div :class="{ 'ms-0': isOpen, 'ms-80': !isOpen }" class="m-5 hover:text-secondary text-white font-normal tracking-wide text-lg transition-all duration-[2500ms] ease-in-out ">
                    <RouterLink to="/">Home</RouterLink>
                </div>
                <div :class="{ 'ms-0': isOpen, 'ms-80': !isOpen }"  class="m-5  hover:text-secondary text-white font-normal tracking-wide text-lg  transition-all duration-[2600ms] ease-in-out">
                    <RouterLink to="/about">About Shanta</RouterLink>
                </div>
                <div :class="{ 'ms-0': isOpen, 'ms-80': !isOpen }"  class="m-5  hover:text-secondary text-white font-normal tracking-wide text-lg transition-all duration-[2700ms] ease-in-out">
                    <RouterLink to="/project">Projcts</RouterLink>
                </div>
                <div :class="{ 'ms-0': isOpen, 'ms-80': !isOpen }"  class="m-5  hover:text-secondary text-white font-normal tracking-wide text-lg transition-all duration-[2900ms] ease-in-out">
                    <RouterLink to="/">Careers</RouterLink>
                </div>
                <div :class="{ 'ms-0': isOpen, 'ms-80': !isOpen }"  class="m-5 hover:text-secondary text-white font-normal tracking-wide text-lg transition-all duration-[3000ms] ease-in-out">
                    <RouterLink to="/news-event">News & Events</RouterLink>
                </div>
                <div :class="{ 'ms-0': isOpen, 'ms-80': !isOpen }"  class="m-5  hover:text-secondary text-white font-normal tracking-wide text-lg transition-all duration-[3100ms] ease-in-out">
                    <RouterLink to="/contact">Contact Us</RouterLink>
                </div>
            </div>
        </div>
    </aside>
 
</template>
<style scoped>
/*-----light button--------*/
.slider:before {
  position: absolute;
  content: "";
  height: 19px;
  width: 18px;
  background-color: #8e8a1f;
  transition: .4s;
}
input:checked + .slider {
  background-color: #b4b269;
}

input:checked + .slider:before {
  transform: translateX(26px);
}

/* Rounded sliders */
.slider.round {
  border-radius: 35px;
}
.slider.round:before {
  border-radius: 50%;
}

/*--------menu button-----------*/

.elegance-hamburger-menu {
  display: inline-flex;
}
.elegance-hamburger-menu .elegance-hamburger-menu__btn--active span {
  transform: rotate(45deg);
}
.elegance-hamburger-menu .elegance-hamburger-menu__btn--active span::before {
  content: "";
  position: absolute;
  top: 0;
  transform: rotate(0);
}
.elegance-hamburger-menu .elegance-hamburger-menu__btn--active span::after {
  content: "";
  position: absolute;
  top: 0;
  transform: rotate(90deg);
}
.elegance-hamburger-menu__btn {
  display: flex;
  align-items: center;
  width: 30px;
  height: 40px;
  position: relative;
  cursor: pointer;
}
.elegance-hamburger-menu__btn span {
  display: block;
  position: absolute;
  width: 100%;
  height:2px;
  transition: all 0.3s ease-in-out;
}
.elegance-hamburger-menu__btn span::before,
.elegance-hamburger-menu__btn span::after {
  content: "";
  display: block;
  position: relative;
  width: 100%;
  height: 2px;
  background-color: #8e8a1f; /* Red-800 */
  transition: all 0.3s ease-in-out;
}
.elegance-hamburger-menu__btn span::before {
  top: -2px;
}
.elegance-hamburger-menu__btn span::after {
  top: 2px;
}



</style>