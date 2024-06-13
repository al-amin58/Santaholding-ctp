<script setup>

import { ref, onMounted } from 'vue';


const isOpen = ref(false);

// for Navbar scroll hidden start--------------------
const lastScrollTop = ref(0);
const scrolledDown = ref(false);
const header = ( () =>{
  window.addEventListener("scroll", handleScroll);
})
onMounted(() => {
  header()
  
});
const handleScroll = () => {
  const scrollTop = window.pageYOffset || document.documentElement.scrollTop;
  scrolledDown.value = scrollTop > lastScrollTop.value;
  lastScrollTop.value = scrollTop;
};
//  Navbar scroll hidden end--------------------

//for manu bar button start---------------------------------
const menuContainer = ref(null);
const menuItemsContainer = ref(null);

const toggleMenu = () => {
  if (menuContainer.value) {
    menuContainer.value.classList.toggle("active");

    if (menuContainer.value.classList.contains("active") && menuItemsContainer.value) {
      menuItemsContainer.value.classList.add("active");
    } else if (menuItemsContainer.value) {
      menuItemsContainer.value.classList.remove("active");
    }
  }
};
//for manu bar button end---------------------------------
</script>

<template>
    <div id="navbar" :class="{ '-top-60': scrolledDown, 'top-0': !scrolledDown }"  class=" opacity-100  z-50 bg-primary fixed flex justify-between w-full top-0 h-[100px] pt-2 px-7.5p items-center transition-all ease-in-out duration-500" >

        <RouterLink to="/">
            <img src="@/assets/images/logo/logo.png" class="w-full h-16">
        </RouterLink>
        <div class="flex items-center gap-5">
            <div class="flex items-center gap-2">
                <h1 class="font-semibold text-xl text-Color uppercase">light</h1>
                <label id="dark" class="switch relative inline-block w-11  h-5 ">
                    <input class="opacity-0 w-0 h-0" type="checkbox">
                    <span class="slider round  absolute cursor-pointer top-0 left-0 right-0 bottom-0 bg-headertogol transition duration-400"></span>
                </label>
            </div>
            <div @click="toggleMenu"  class="elegance-hamburger-menu flex justify-center items-center gap-2  cursor-pointer ">
              <div>
                <h2 @click="isOpen = true" class="font-semibold text-xl text-Color uppercase hover:text-secondary">Menu</h2>
              </div>  
                <div @click="isOpen = true" class="menu-container" ref="menuContainer">
                  <div class="line line-1">
                    <div class="line-inner line-inner-1"></div>
                  </div>
                  <div class="line line-2">
                    <div class="line-inner line-inner-2"></div>
                  </div>
                </div>
            </div>
        </div>
    </div>
  
      <aside  :class="{ 'right-0': isOpen , ' -right-[600px]': !isOpen }" class="opacity-100  z-50 transition-all ease-in-out duration-1000 fixed  bg-manubar opacity-96 w-full h-screen max-w-lg top-0  bottom-0  overflow-auto " >
        <div class="text-white ms-5 mt-2">
            <div class="mt-10 ps-10">
              <div :class="{ 'ms-80': isOpen, 'ms-0': !isOpen }"  class="flex  pe-10  transition-all ease-in-out duration-[1000ms]">
                  <div @click="toggleMenu"  class="elegance-hamburger-menu flex justify-center items-center gap-2  cursor-pointer ">
                    <h2 @click="isOpen = false" class="font-semibold text-xl text-white uppercase hover:text-gray-100">Close</h2>
                    <div @click="isOpen = false" class="menu-container" ref="menuContainer">
                      <div class="line line-1">
                        <div class="line-inner line-inner-1" style="background: white !important;"></div>
                      </div>
                      <div class="line line-2">
                        <div class="line-inner line-inner-2 " style="background: white !important;"></div>
                      </div>
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

/*--------- for menu button start---------*/

.menu-container {
  cursor: pointer;
}

.menu-container .line {
  height: 30px;
  width: 30px;
  top: 40px;
  position: absolute;
  transition: transform 300ms ease-in-out;
}

.menu-container .line-inner {
  height: 2px;
  width: 30px;
  background: #8e8a1f;
  border-radius: 4px;
  position: absolute;
  transition: transform 200ms ease-in-out;
  transition-delay: 200ms;
}

.menu-container .line-inner-1 {
  top: 15px;
  transform: translateY(-5px);
}
.menu-container .line-inner-2 {
  bottom: 15px;
  transform: translateY(5px);
}

.menu-container.active .line-1 {
  transform: rotateZ(45deg);
}

.menu-container.active .line-2 {
  transform: rotateZ(-45deg);
}

.menu-container.active .line-inner {
  transform: none;
  transition: transform 200ms ease-in-out;
}

.menu-container.active .line {
  transition-delay: 200ms;
}


</style>