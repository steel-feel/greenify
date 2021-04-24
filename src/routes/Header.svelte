<script>
//import { element } from "svelte/internal";


var m = true;


function handleClick (){
   m = !m;
}

</script>

<style>
.hideclass{
    visibility: hidden;
    width: 0;
    height: 0;
}

</style>


<nav class="flex items-center justify-between flex-wrap bg-gray-200 p-4">
    <div class="flex items-center flex-shrink-0 text-black mr-6">
      <!-- <svg class="fill-current h-8 w-8 mr-2" width="54" height="54" viewBox="0 0 54 54" xmlns="http://www.w3.org/2000/svg"><path d="M13.5 22.1c1.8-7.2 6.3-10.8 13.5-10.8 10.8 0 12.15 8.1 17.55 9.45 3.6.9 6.75-.45 9.45-4.05-1.8 7.2-6.3 10.8-13.5 10.8-10.8 0-12.15-8.1-17.55-9.45-3.6-.9-6.75.45-9.45 4.05zM0 38.3c1.8-7.2 6.3-10.8 13.5-10.8 10.8 0 12.15 8.1 17.55 9.45 3.6.9 6.75-.45 9.45-4.05-1.8 7.2-6.3 10.8-13.5 10.8-10.8 0-12.15-8.1-17.55-9.45-3.6-.9-6.75.45-9.45 4.05z"/></svg> -->
      <img src="./logo.png" class=" h-8 w-8 mr-2" alt="">
      <span class="font-semibold text-xl tracking-tight">Greenify</span>
    </div>
    <div class="block md:hidden ">
      <a on:click={handleClick}  class="cursor-pointer flex items-center px-3 py-2 border rounded text-black-100 border-gray-200 ">
        <svg class="fill-current h-4 w-4" viewBox="0 0 20 20" xmlns="http://www.w3.org/2000/svg"><title>Menu</title><path d="M0 3h20v2H0V3zm0 6h20v2H0V9zm0 6h20v2H0v-2z"/></svg>
      </a>
    </div>
    <div id="mobile-menu" class:hideclass="{m}" class="transition-all fixed right-0 top-0 h-screen my-1 w-2/3 z-7 block flex-grow md:flex bg-gray-500 md:justify-end md:w-auto">
        <a on:click={handleClick}  class="float-right clear-right my-3 cursor-pointer flex items-center px-3 py-2 text-white border-gray-200 ">
            <svg xmlns="http://www.w3.org/2000/svg" width="20.953" height="20.953" viewBox="0 0 20.953 20.953">
                <path id="Icon_ionic-md-close" data-name="Icon ionic-md-close" d="M28.477,9.619l-2.1-2.1L18,15.9,9.619,7.523l-2.1,2.1L15.9,18,7.523,26.381l2.1,2.1L18,20.1l8.381,8.381,2.1-2.1L20.1,18Z" transform="translate(-7.523 -7.523)" fill="#fff"/>
              </svg>
            </a>
        <div>
        <a href="#" on:click={handleClick} class="no-underline  font-bold block md:inline-block text-md px-4 py-2 leading-none rounded text-white border-white hover:border-transparent hover:text-teal-500  mt-4 md:mt-0">Home</a>
         <a href="#"  on:click={handleClick} class="no-underline  font-bold block md:inline-block text-md px-4 py-2 leading-none rounded text-white border-white hover:border-transparent hover:text-teal-500  mt-4 md:mt-0">How-tos</a>
         <a href="#" on:click={handleClick}  class="no-underline  font-bold block md:inline-block text- px-4 py-2 leading-none rounded text-white border-white hover:border-transparent hover:text-teal-500  mt-4 md:mt-0">Trasaction History</a>
      </div>
    </div>
  </nav>
  