<template>
  <div
    class="hidden lg:flex flex-col xl:w-1/4 lg:w-1/3 h-full sticky trend"
    style=""
  >
    <div class="mt-2">
      <input
        class="border border-transparent rounded-full w-full bg-gray-200 h-11 text-sm mb-4 pl-14 font-normal text-green-400 focus:outline-none focus:ring-1 focus:ring-purple-400 focus:border-transparent focus:bg-white focus:text-blue-500"
        placeholder="Search Twitter"
      />

      <i
        class="fa fa-search absolute left-0 top-0 ml-6 mt-5 text-md text-gray-500 font-normal"
      ></i>
    </div>
    <div class="rounded-md bg-gray-100">
      <div class="flex flex-row justify-between mt-2 mx-4 mb-3">
        <h1 class="font-semibold text-lg">Trends for you</h1>
        <i class="fa fa-cog text-blue-500 text-2xl" aria-hidden="true"></i>
      </div>
      <div
        class="border-t border-lighter hover:bg-gray-200"
        v-for="trend in trends"
        :key="trend.id"
      >
        <div class="mt-3 flex flex-row justify-between mx-4">
          <div class="flex flex-col space-y-1 mb-2">
            <p class="text-xs text-gray-600">{{ trend.trending }}</p>
            <h1 class="font-semibold text-sm">{{ trend.topic }}</h1>
            <p class="text-xs text-gray-600">{{ trend.tweets }}</p>
          </div>
          <span><i class="fa fa-ellipsis-h" aria-hidden="true"></i></span>
        </div>
      </div>
      <div class="border-t border-lighter">
        <p class="text-blue-400 mt-3 mx-4 mb-3 text-sm">Show more</p>
      </div>
    </div>

    <div class="rounded-md bg-gray-100 mt-3">
      <div class="mt-2 mx-4 mb-4">
        <h1 class="font-semibold text-lg">Who to follow</h1>
      </div>
      <div
        class="border-t border-lighter hover:bg-gray-200"
        v-for="follow in follows"
        :key="follow.id"
      >
        <div class="mt-3 flex flex-row justify-between mx-4">
          <div class="flex flex-row space-x-2">
            <img
              :src="`src/assets/${follow.profile}`"
              alt=""
              class="w-12 h-12 rounded-full"
            />
            <div class="flex flex-col space-y-1 mb-2">
              <h1 class="font-semibold text-sm">{{ follow.name }}</h1>
              <p class="text-xs text-gray-600">{{ follow.username }}</p>
            </div>
          </div>
          <button
            class="w-20 h-9 border border-blue-400 rounded-full bg-transparent text-blue-500 font-medium tweet hover:bg-gray-300"
            style=""
          >
            Follow
          </button>
        </div>
      </div>
      <div class="border-t border-lighter">
        <p class="text-blue-400 mt-3 mx-4 mb-3 text-sm">Show more</p>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  data() {
    return {
      trends: [
        {
          id: 1,
          trending: "Trending in Nepal",
          topic: "Nepal",
          tweets: "11.7k Tweets",
        },
        {
          id: 2,
          trending: "Trending in Nepal",
          topic: "#GenerationEquality",
          tweets: "11.7k Tweets",
        },
        {
          id: 3,
          trending: "Trending in Nepal",
          topic: "#InternationalWomensDay",
          tweets: "10k Tweets",
        },
        {
          id: 4,
          trending: "Politics . Trending ",
          topic: "#ChooseToChallenge",
          tweets: "11.7k Tweets",
        },
        {
          id: 5,
          trending: "Business & finance · Trending",
          topic: "#womenpower",
          tweets: "11.7k Tweets",
        },
      ],
      follows: [
        { id: 1, profile: "guna.jpg", name: "Huwaei", username: "@Huwaei" },
        {
          id: 2,
          profile: "rocket.jpg",
          name: "David luhr",
          username: "@david_luhr",
        },
      ],
    };
  },
};
</script>
<style scoped>
.trend {
  margin-left: 2%;
}
</style>