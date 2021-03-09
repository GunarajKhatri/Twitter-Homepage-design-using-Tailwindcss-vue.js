<template>
  <div
    class="xl:w-1/2 h-full mt-0 border-r border-lighter maincontent1"
    id="maincontent"
    style=""
  >
    <div class="sticky top-0 bg-white">
      <!--margin-left:22.3%; -->
      <div class="flex mt-3 ml-4">
        <h1 class="font-medium text-lg">Home</h1>
      </div>
      <div class="mt-3 border-b border-lighter"></div>
    </div>
    <div class="ml-4 mt-2 flex flex-row">
      <div class="xl:space-x-3">
        <img
          src="/src/assets/guna.jpg"
          alt="Guna"
          class="w-12 h-12 rounded-full"
        />
      </div>
      <div class="flex flex-col">
        <textarea
          class="mt-3 xl:ml-2 xl:space-y-3"
          v-model="tweet"
          style="border: none; outline: none; resize: none"
          cols="20"
          placeholder="What's happening?"
        ></textarea>
        <div class="flex flex-row ml-2 w-full">
          <div class="space-x-4 sm:space-x-4 lg:space-x-5 mt-2">
            <span
              v-for="menu in menus"
              :key="menu.id"
              class="text-blue-400 text-lg lg:text-xl border border-transparent rounded-full hover:bg-gray-200"
              ><i :class="menu.icon"></i
            ></span>
          </div>
          <button
            class="lg:ml-78 xl:ml-80 ml-72 w-20 h-10 rounded-full bg-blue-300 text-white font-medium tweet"
            style=""
          >
            Tweet
          </button>
        </div>
      </div>
    </div>
    <div class="mt-3 mb-3 border-b border-lighter"></div>
    <!-- <div class="mt-0 border-b border-lighter"></div> -->

    <div
      class="border-t border-lighter hover:bg-gray-100"
      v-for="tweet in tweets"
      :key="tweet.id"
    >
      <div class="flex flex-row ml-4 space-x-2 mt-3">
        <img
          :src="`src/assets/${tweet.profilepic}`"
          alt=""
          class="w-12 h-12 rounded-full"
        />
        <div class="flex flex-col space-y-0">
          <div class="flex space-x-1">
            <h1 class="text-md font-medium">{{ tweet.name }}</h1>
            <p class="text-sm text-gray-500">
              {{ tweet.username }} . {{ tweet.time }}
            </p>
          </div>
          <div class="mb-3">
            <p class="text-sm font-normal">
              {{ tweet.tweetPost }}
            </p>
            <img
              v-if="tweet.photo != ''"
              class="h-72 rounded-xl mt-2 tweetpic"
              :src="`src/assets/${tweet.photo}`"
              alt=""
            />
          </div>
          <div class="flex flex-row justify-between mr-1 tweetbtn" style="">
            <span
              class="text-gray-400 text-md mt-2"
              v-for="btn in btns"
              :key="btn.id"
              ><i
                :class="btn.icon"
                style="
                  color: transparent;
                  -webkit-text-stroke-width: 1px;
                  -webkit-text-stroke-color: gray;
                "
              ></i
            ></span>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  data() {
    return {
      windowWidth: window.innerWidth,
      tweet: "",
      menus: [
        { icon: "fa fa-picture-o", id: 1 },
        // {icon:'fas fa-film',id:2},
        { icon: "fa fa-bar-chart", id: 3 },
        { icon: "fa fa-smile-o", id: 4 },
        { icon: "fa fa-calendar", id: 5 },
      ],
      btns: [
        { icon: "fa fa-comments", id: 1 },
        { icon: "fa fa-retweet", id: 3 },
        { icon: "fa fa-heart", id: 4 },
        { icon: "fa fa-share-square-o", id: 5 },
      ],
      tweets: [
        {
          id: 1,
          name: "Lex Fridman",
          username: "@lexfridman",
          profilepic: "fridman.jpg",
          time: "1hr",
          tweetPost:
            '"We choose to go to the Moon in this decade and do the other things, not because they are easy, but because they are hard." - John F. Kennedy',
          photo: "interview.jpeg",
        },
        {
          id: 2,
          name: "Elon musk",
          username: "@elonmusk",
          profilepic: "rocket.jpg",
          time: "Feb 25",
          tweetPost: "Horses are even self-driving!",
          photo: "horse.jpeg",
        },
        {
          id: 3,
          name: "Elon musk",
          username: "@elonmusk",
          profilepic: "rocket.jpg",
          time: "Feb 25",
          tweetPost: "I admit to judging books by their cover",
          photo: "",
        },
      ],
    };
  },
  watch: {
    windowWidth(newWidth, oldWidth) {
      if (newWidth < 704) {
        this.menus = [
          { icon: "fa fa-picture-o", id: 1 },
          { icon: "fa fa-smile-o", id: 4 },
          { icon: "fa fa-calendar", id: 5 },
        ];
      } else {
        this.menus = [
          { icon: "fa fa-picture-o", id: 1 },
          { icon: "fa fa-bar-chart", id: 3 },
          { icon: "fa fa-smile-o", id: 4 },
          { icon: "fa fa-calendar", id: 5 },
        ];
      }
    },
  },
  mounted() {
    this.$nextTick(() => {
      window.addEventListener("resize", this.onResize);
    }),
      this.check();
  },
  beforeDestroy() {
    window.removeEventListener("resize", this.onResize);
  },
  methods: {
    onResize() {
      this.windowWidth = window.innerWidth;
    },
    check() {
      if (this.windowWidth < 704) {
        this.menus = [
          { icon: "fa fa-picture-o", id: 1 },
          { icon: "fa fa-smile-o", id: 4 },
          { icon: "fa fa-calendar", id: 5 },
        ];
      }
    },
  },
};
</script>
<style scoped>
.tweetpic {
  width: 98%;
}
#maincontent {
  margin-left: 22.1%;
}
.tweetbtn {
  width: 450px;
}
@media screen and (max-width: 1356px) {
  #maincontent {
    margin-left: 21%;
    
  }
}
@media screen and (max-width: 1279px) {
  #maincontent {
    margin-left: 70px;
    width: 62%;
  }
}

@media screen and (max-width: 1023px) {
  #maincontent {
    width: 82%;
  }
}
@media screen and (max-width: 767px) {
  #maincontent {
    width: 100%;
  }

}
@media screen and (max-width: 614px) {
  #maincontent {
    margin-left: 68px;
    width: 87%;
  }
  .tweet {
    margin-left: 10%;
  }
}
@media screen and (max-width: 609px) {
  .tweetpic {
    width: 93%;
  }
  .tweetbtn {
    width: 350px;
  }
}
@media screen and (max-width: 528px) {
  .tweetbtn {
    width: 300px;
  }
}
</style>
