<template>
  <div class="wrapper">
    <div class="container">
      <div class="post">
        <div class="account-info">
          <div class="person">
            <img src="./images/Avatar.svg" alt="">
            <p>terrylucas</p>
          </div>
          <div class="more"><img src="./images/More.svg" alt=""></div>
        </div>
        <div class="post-image">
          <img @dblclick="switchLike()" src="./images/post.png" alt="postImage">
        </div>
        <div class="post-info">
          <div class="selector-icons">
            <div class="icons-left">
              <img class="like" @click="switchLike()" :src="likeSrc"  alt="like">
              <img class="center-img" src="./images/Comment.svg" alt="">
              <img src="./images/SharePosts.svg" alt="">
            </div>
            <div class="icons-right">
              <img @click="switchSave()" :src="saveSrc" alt="save">
            </div>
          </div>
          <div class="likes">
            <p class="like-num">{{ likenum }}</p><p class="like-text">like</p>
          </div>
          <div class="desc">
            <p class="username">terrylucas</p>
            <p class="desc-text">Imperdiet in sit rhoncus...</p>
          </div>
          <div class="add-comment">
            <img src="./images/Emoji.svg" alt="">
            <input type="text"  @keyup.enter="addItem" v-model="newItem" placeholder="Add a comment...">
            <span @click="addItem">Post</span>
          </div>
          <div class="comments">
            <ul class="items" :key="item" v-for="item in reversedItems">
              <li class="item">
                <div class="info">
                  <span class="item-name">{{ item.name }}</span>
                </div>
              </li>
            </ul>
          </div>
        </div>
      </div>
    </div>
  </div>

</template>

<script>

export default {
  name: "App",

  data() {
    return {
      newItem: '',
      items: [

      ],
      likenum: 1961,
      likeSrc: "https://cdn-icons.flaticon.com/png/128/2961/premium/2961957.png?token=exp=1644583360~hmac=6edff6b7fa6e8b78f726687be3959c9e",
      saveSrc: "https://cdn-icons.flaticon.com/png/128/5662/premium/5662990.png?token=exp=1644583412~hmac=06c6e96d17dda289832b5316101a4957",
    }
  },

  computed: {
    reversedItems() {
      return this.items.slice();
    },
  },

  methods: {
    addItem: function () {
        this.items.push({
            id: this.items.length + 1,
            name: this.newItem,
        });
        this.newItem = '';
    },

    switchLike() {
      this.likeSrc = "https://cdn-icons-png.flaticon.com/128/833/833472.png",
      this.likenum++
    },

    switchSave() {
      this.saveSrc = "https://cdn-icons-png.flaticon.com/128/102/102279.png"
    }

  }

};

</script>

<style src="./style/main.css">

</style>
