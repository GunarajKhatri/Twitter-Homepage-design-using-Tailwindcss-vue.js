<template>
  <div
    class="fixed flex flex-col overflow-y-auto overflow-x-hidden h-full mt-0 w-16 xl:w-1/5 border-r border-lighter xl:ml-3 ml-2"
  >
    <span
      class="w-12 h-12 rounded-full border-tranparent hover:bg-gray-100 text-blue-400 text-3xl mt-2 mb-1 pl-3 pt-1"
      ><i class="fa fa-twitter" aria-hidden="true"></i
    ></span>
    <div v-for="sidebar in sidebars" :key="sidebar.id">
      <button
        v-if="sidebar.id == 1"
        class="items-center mr-2 xl:pr-3 border border-transparent rounded-full hover:bg-gray-100"
      >
        <div class="flex flex-row space-x-2">
          <span
            class="w-12 h-12 text-blue-400 text-2xl pt-2 hover:text-blue-400"
            ><i :class="sidebar.icon" aria-hidden="true"></i
          ></span>

          <h2 class="text-lg font-medium text-blue-400 pt-2 hidden xl:block">
            {{ sidebar.text }}
          </h2>
        </div>
      </button>
      <button
        class="items-center mr-2 xl:pr-3 border border-transparent rounded-full hover:bg-gray-100 hover:text-blue-400"
        v-else
      >
        <div class="flex flex-row space-x-2">
          <span class="w-12 h-12 text-2xl hover:text-blue-400 pt-2"
            ><i
              :class="sidebar.icon"
              aria-hidden="true"
              style="
                color: transparent;
                -webkit-text-stroke-width: 2px;
                -webkit-text-stroke-color: black;
              "
            ></i
          ></span>

          <h2 class="text-lg font-medium pt-2 hidden xl:block">
            {{ sidebar.text }}
          </h2>
        </div>
      </button>
    </div>
    <button
      class="hidden xl:block bg-blue-400 text-center py-3 mt-2 mr-8 max-w-sm rounded-full text-white font-normal hover:bg-blue-500"
    >
      Tweet
    </button>
    <span
      class="xl:hidden mt-1 py-3 px-4 w-12 h-12 rounded-full bg-blue-400 text-white hover:bg-blue-500"
      ><i class="fa fa-plus-circle" aria-hidden="true"></i
    ></span>
    <div
      class="mt-28 flex flex-row xl:mt-28 text-md rounded-full border border-transparent hover:bg-gray-100 w-64 h-14"
    >
      <div class="block xl:space-x-3">
        <img
          src="/src/assets/guna.jpg"
          alt="Guna"
          class="w-10 h-10 rounded-full"
        />
      </div>
      <div class="hidden xl:flex flex-col">
        <h2 class="text-md font-bold">Gunaraj khatri</h2>
        <p class="text-gray-500 mt-0">@khatri_guna</p>
      </div>

      <span class="hidden xl:block ml-16 mt-4"
        ><i class="fa fa-ellipsis-h" aria-hidden="true"></i
      ></span>
    </div>
  </div>
</template>
<script>
export default {
  data() {
    return {
      sidebars: [
        { icon: "fa fa-home ", text: "Home", id: "1" },
        { icon: "fa fa-hashtag", text: "Explore", id: "2" },
        { icon: "fa fa-bell", text: "Notifications", id: "3" },
        { icon: "fa fa-envelope", text: "Messages", id: "4" },
        { icon: "fa fa-user", text: "Profile", id: "5" },
        { icon: "fa fa-ellipsis-h", text: "More", id: "6" },
      ],
    };
  },
};
</script>